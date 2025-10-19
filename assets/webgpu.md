WebGPU Forward+ and Clustered Deferred Shading
======================

**University of Pennsylvania, CIS 565: GPU Programming and Architecture, Project 4**

* Yiding Tian
* Tested on: **Google Chrome 141.0.7390.108** on
  Windows 11, i9-13900H @ 4.1GHz 32GB, RTX 5080 16GB (Personal laptop with external desktop GPU via NVMe connector running in PCIe 4.0x4)

### Live Demo

[![](img/thumb.png)](http://webgpu.tonyxtian.com)

[**Click to view live demo deployed at webgpu.tonyxtian.com**](http://webgpu.tonyxtian.com)

### Demo Video

[Demo Video (MP4)](img/webgpu_demo.mp4)

## Project Overview

This project implements Forward+ and Clustered Deferred rendering techniques using WebGPU. The application renders the Sponza Atrium scene with a large number of dynamic point lights, demonstrating the performance benefits of clustered lighting approaches over naive forward rendering.

### Implemented Features

#### Core Features
- **Naive Forward Renderer** 
  - Basic forward rendering with camera view projection matrix
  - All lights evaluated for every fragment
  - Baseline for performance comparison

- **Forward+ Renderer** 
  - Screen-space light clustering using compute shader
  - 3D grid of clusters in view frustum
  - Light culling per cluster to reduce per-fragment light evaluations
  - Efficient data structure for tracking light indices per cluster

- **Clustered Deferred Renderer** 
  - G-buffer with three render targets:
    - Position buffer (rgba16float)
    - Normal buffer (rgba16float)
    - Albedo buffer (rgba8unorm)
  - Reuses clustering logic from Forward+
  - Two-pass rendering: geometry pass and fullscreen lighting pass
  - Decouples geometry complexity from lighting complexity

#### Extra Features

- **Automated Performance Testing System**
  - Comprehensive benchmark runner that automatically tests all rendering modes
  - Systematically varies light count from 500 to 5000 in 500-light increments
  - Collects statistical data (average, minimum, maximum frame times)
  - Real-time progress display showing test status and intermediate results
  - Automatic CSV generation and download for easy data analysis
  - Used to generate all performance data in this README

## Implementation Details

This section explains the technical implementation of each rendering technique.

### Naive Forward Rendering

The naive forward renderer serves as the baseline implementation:

**Vertex Shader:**
- Transforms vertex positions from model space to clip space using model-view-projection matrix
- Passes world-space position, normal, and UV coordinates to fragment shader

**Fragment Shader:**
- For each fragment, iterates through **all lights** in the scene
- For each light:
  - Calculates distance attenuation: `intensity / (distance²)`
  - Computes diffuse lighting using Lambert's cosine law: `max(dot(normal, lightDir), 0)`
  - Accumulates contribution to final color
- Applies texture color and outputs final result

**Performance characteristics:**
- Time complexity: O(fragments × lights)
- No optimization - every fragment tests every light
- Becomes bottlenecked as light count increases

### Forward+ Rendering

Forward+ improves on naive rendering by using light clustering to reduce the number of lights evaluated per fragment.

#### Light Clustering

The view frustum is subdivided into a 3D grid of clusters. Each cluster tracks which lights affect its volume, allowing fragments to only evaluate relevant lights.

![Light Clustering Visualization](img/clustering-eg.png)
*Figure: Light clustering visualization showing the 3D grid subdivision of the view frustum. Colored spheres represent light volumes, and only lights intersecting a cluster are evaluated for fragments within that cluster. (Image credit: [Adrián Ortiz - Tile/Clustered Shading](https://www.aortiz.me/2018/12/21/CG.html#tiled-shading--forward))*

**Clustering Compute Shader** ([clustering.cs.wgsl](src/shaders/clustering.cs.wgsl)):

1. **Cluster AABB Calculation:**
   ```wgsl
   // Calculate cluster bounds in view space
   let tileSize = vec2f(screenWidth / clusterWidth, screenHeight / clusterHeight);
   let minScreen = vec2f(clusterID.xy) * tileSize;
   let maxScreen = vec2f(clusterID.xy + 1) * tileSize;

   // Convert screen-space corners to view space rays
   let nearDepth = camera.near * pow(camera.far / camera.near, clusterID.z / clusterDepth);
   let farDepth = camera.near * pow(camera.far / camera.near, (clusterID.z + 1) / clusterDepth);
   ```
   - Grid dimensions: 16×9×24 clusters (width × height × depth)
   - Depth slices use exponential distribution for better precision near camera
   - Each cluster stores min/max bounds as AABBs

2. **Light Assignment:**
   ```wgsl
   // For each light, test intersection with cluster AABB
   for (var lightIdx = 0u; lightIdx < numLights; lightIdx++) {
       let lightPos = lights[lightIdx].pos;
       let lightRadius = lights[lightIdx].radius;

       if (sphereAABBIntersection(lightPos, lightRadius, clusterMin, clusterMax)) {
           // Add light index to this cluster's light list
           let offset = atomicAdd(&lightGrid[clusterIdx].count, 1u);
           globalLightIndexList[clusterIdx * maxLightsPerCluster + offset] = lightIdx;
       }
   }
   ```
   - Each cluster maintains a count of intersecting lights
   - Light indices stored in a global list with per-cluster offsets
   - Maximum 256 lights per cluster (configurable)

**Data Structures:**
- `lightGrid`: Array of cluster metadata (light count + offset)
- `globalLightIndexList`: Flat array of light indices
- `clusterAABBs`: Bounding boxes for each cluster

**Fragment Shader** ([forward_plus.fs.wgsl](src/shaders/forward_plus.fs.wgsl)):

```wgsl
// Determine which cluster this fragment belongs to
let clusterID = getClusterID(fragPos, screenPos);
let clusterIdx = clusterID.x + clusterID.y * clusterWidth + clusterID.z * clusterWidth * clusterHeight;

// Retrieve lights for this cluster
let lightCount = lightGrid[clusterIdx].count;
let lightOffset = lightGrid[clusterIdx].offset;

// Only iterate through lights affecting this cluster
for (var i = 0u; i < lightCount; i++) {
    let lightIdx = globalLightIndexList[lightOffset + i];
    let light = lights[lightIdx];
    // ... perform lighting calculation
}
```

**Advantages over Naive:**
- Dramatically reduces light evaluations per fragment
- Clustering overhead amortized across all fragments
- Enables thousands of lights in real-time

### Clustered Deferred Rendering

Clustered Deferred decouples geometry processing from lighting by using a G-buffer to store surface properties, then performing lighting in a separate fullscreen pass.

#### G-Buffer Pass

**Vertex Shader** ([naive.vs.wgsl](src/shaders/naive.vs.wgsl) - reused):
- Same as naive renderer
- Transforms geometry to clip space

**Fragment Shader** ([clustered_deferred.fs.wgsl](src/shaders/clustered_deferred.fs.wgsl)):
```wgsl
struct GBufferOutput {
    @location(0) position: vec4f,  // World position + depth
    @location(1) normal: vec4f,    // World normal
    @location(2) albedo: vec4f     // Texture color
}

@fragment
fn main(input: VertexOutput) -> GBufferOutput {
    var output: GBufferOutput;
    output.position = vec4f(input.worldPos, input.depth);
    output.normal = vec4f(normalize(input.normal), 1.0);
    output.albedo = textureSample(diffuseTex, diffuseSampler, input.uv);
    return output;
}
```

**G-Buffer Layout:**
- **Position buffer** (rgba16float): Stores world-space position and depth
- **Normal buffer** (rgba16float): Stores world-space normal vectors
- **Albedo buffer** (rgba8unorm): Stores base texture color
- Total: 12 bytes per pixel

#### Fullscreen Lighting Pass

**Vertex Shader** ([clustered_deferred_fullscreen.vs.wgsl](src/shaders/clustered_deferred_fullscreen.vs.wgsl)):
```wgsl
@vertex
fn main(@builtin(vertex_index) vertexIndex: u32) -> VertexOutput {
    // Generate fullscreen triangle
    let pos = array<vec2f, 6>(
        vec2f(-1.0, -1.0), vec2f(1.0, -1.0), vec2f(-1.0, 1.0),
        vec2f(-1.0, 1.0), vec2f(1.0, -1.0), vec2f(1.0, 1.0)
    );
    return VertexOutput(vec4f(pos[vertexIndex], 0.0, 1.0), pos[vertexIndex]);
}
```
- Generates fullscreen quad without vertex buffer
- Outputs clip-space coordinates directly

**Fragment Shader** ([clustered_deferred_fullscreen.fs.wgsl](src/shaders/clustered_deferred_fullscreen.fs.wgsl)):
```wgsl
@fragment
fn main(@builtin(position) screenPos: vec4f, @location(0) uv: vec2f) -> @location(0) vec4f {
    // Sample G-buffer
    let position = textureLoad(gBufferPosition, screenCoord, 0);
    let normal = textureLoad(gBufferNormal, screenCoord, 0);
    let albedo = textureLoad(gBufferAlbedo, screenCoord, 0);

    // Get cluster for this pixel
    let clusterID = getClusterID(position.xyz, screenPos.xy);

    // Perform lighting using clustered light list
    var totalLight = vec3f(0.0);
    let lightCount = lightGrid[clusterIdx].count;
    for (var i = 0u; i < lightCount; i++) {
        let lightIdx = globalLightIndexList[lightOffset + i];
        // ... accumulate lighting
    }

    return vec4f(albedo.rgb * totalLight, 1.0);
}
```

**Key Advantages:**
- **Decoupled complexity**: Geometry pass independent of light count
- **No overdraw waste**: Only visible pixels are shaded
- **Memory coherency**: Fullscreen pass has optimal cache behavior
- **Constant work per pixel**: Each pixel shaded exactly once

#### Comparison: Forward+ vs Clustered Deferred

| Aspect | Forward+ | Clustered Deferred |
|--------|----------|-------------------|
| **Passes** | 1 (geometry + lighting) | 2 (G-buffer + lighting) |
| **Overdraw** | Shades occluded fragments | Only shades visible pixels |
| **Memory** | Lower (no G-buffer) | Higher (G-buffer textures) |
| **Bandwidth** | Lower (no texture writes) | Higher (write + read G-buffer) |
| **Transparency** | Fully supported | Difficult (single depth) |
| **Performance** | Good for simple scenes | Best for complex scenes |

### Implementation Techniques

**Exponential Depth Slicing:**
Clusters use exponential depth distribution to match perspective projection:
```wgsl
let depthSlice = log(viewDepth / near) / log(far / near) * numSlices;
```
This provides more precision near the camera where most detail exists.

**Atomic Operations for Light Assignment:**
```wgsl
let offset = atomicAdd(&lightGrid[clusterIdx].count, 1u);
```
Enables parallel cluster assignment without race conditions.

**Struct Alignment:**
All GPU buffers follow WebGPU alignment rules (16-byte boundaries for vec3, etc.) verified using the [WGSL Offset Calculator](https://webgpufundamentals.org/webgpu/lessons/resources/wgsl-offset-computer.html).

### Automated Performance Testing System

To enable rigorous performance analysis, I implemented a comprehensive automated benchmarking system that can test all rendering modes across various configurations without manual intervention.

**Single-click UI:**
A "Start Testing" button in the GUI control panel initiates automated benchmarks. The system displays real-time progress and downloads a timestamped CSV file when complete.

**Test Configuration:**
- **Renderers tested**: Naive, Forward+, Clustered Deferred (all three modes)
- **Light counts**: 500, 1000, 1500, 2000, 2500, 3000, 3500, 4000, 4500, 5000
- **Total configurations**: 30 (3 renderers × 10 light counts)

**For each configuration:**
1. Automatically switches to the target renderer
2. 200ms initialization delay
3. 30 frame warmup to stabilize performance
4. 120 frames of timing data collected
5. Statistical analysis (average, minimum, maximum)

**Frame Time Measurement:**

The system measures **actual frame time** - the time between consecutive frames - rather than just GPU command submission time:

```typescript
// In renderer.ts - measures real frame time
private onFrame(time: number) {
    // ... camera and light updates ...
    this.draw(); // Submit GPU commands
    const frameTime = time - this.prevFrameTime; // Actual frame time
    if (frameTimeCallback) {
        frameTimeCallback(frameTime); // Report to benchmark system
    }
}
```

This approach captures:
- CPU overhead (scene updates, command encoding)
- GPU execution time (actual rendering work)
- Synchronization delays (CPU waiting for GPU)
- True end-to-end performance as experienced by users

**CSV Output Format:**
```csv
Render Mode,Number of Lights,Average Frame Time (ms),Min Frame Time (ms),Max Frame Time (ms)
naive,500,52.345,8.123,1108.456
forward+,500,8.321,8.234,10.123
clustered deferred,500,8.312,8.201,9.876
...
```

## Performance Analysis

All benchmarks were conducted on an RTX 5080 16GB GPU using the automated testing system. The display connected has a frame rate of 120Hz thus capping the maximum possible fps to 120. Frame times are measured in milliseconds (lower is better).

### Summary

| Renderer | 500 Lights | 2000 Lights | 5000 Lights | Speedup vs Naive (5000) |
|----------|------------|-------------|-------------|------------------------|
| **Naive** | 52.3ms (19 FPS) | 199.3ms (5 FPS) | 497.2ms (2 FPS) | 1x baseline |
| **Forward+** | 8.3ms (120 FPS) | 16.0ms (63 FPS) | 32.8ms (30 FPS) | **15.1x faster** |
| **Clustered Deferred** | 8.3ms (120 FPS) | 8.3ms (120 FPS) | 9.3ms (107 FPS) | **53.4x faster** |

### Scaling Analysis

![Performance Comparison](img/performance_comparison.png)
*Figure 1: Frame time scaling and speedup comparison. Top chart shows linear degradation for Naive, sublinear for Forward+, and near-constant for Clustered Deferred. Bottom chart quantifies speedup factors relative to Naive.*

**Key Observations:**

**Naive Renderer** - Linear O(fragments × lights) complexity:
- 10x more lights = ~9.5x slower performance
- At 5000 lights: 497ms average (2 FPS), completely unplayable
- Every fragment evaluates every light regardless of influence

**Forward+ Renderer** - Sublinear scaling via clustering:
- 10x more lights = only 4x slower (8.3ms → 32.8ms)
- Maintains 30 FPS even at 5000 lights
- Light clustering dramatically reduces per-fragment light evaluations
- **15x faster than Naive** at high light counts

**Clustered Deferred Renderer** - Near-constant performance:
- Maintains ~8-9ms across all light counts (500-5000)
- **53x faster than Naive** at 5000 lights, **3.5x faster than Forward+**
- Performance independent of light count in tested range
- Decoupled geometry and lighting: G-buffer pass + fullscreen shading pass
- Only shades visible pixels once, eliminating overdraw waste

### Performance Stability

![Performance Variance](img/performance_variance.png)
*Figure 2: Frame time variance with min/max ranges (shaded areas). Clustered Deferred shows the most consistent performance.*

Frame time consistency is critical for smooth user experience:
- **Naive**: Extreme variance (8ms min, 1108ms max) causes severe stuttering
- **Forward+**: Moderate variance (8ms min, 50ms max) provides mostly smooth experience
- **Clustered Deferred**: Low variance (8ms min, 17ms max) delivers consistently smooth performance

### Why Clustered Deferred Wins

Despite sharing clustering logic with Forward+, Clustered Deferred is 3.5x faster due to:

1. **Overdraw elimination**: Forward+ wastes work on occluded fragments; Deferred only shades final visible pixels
2. **Decoupled passes**: Geometry complexity doesn't affect lighting cost
3. **Memory efficiency**: Fullscreen pass has optimal cache access patterns
4. **Constant work**: Each pixel shaded exactly once regardless of scene complexity

### Credits

- [Vite](https://vitejs.dev/)
- [loaders.gl](https://loaders.gl/)
- [dat.GUI](https://github.com/dataarts/dat.gui)
- [stats.js](https://github.com/mrdoob/stats.js)
- [wgpu-matrix](https://github.com/greggman/wgpu-matrix)