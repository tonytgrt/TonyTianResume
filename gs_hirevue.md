# Goldman Sachs Engineering Analyst - HireVue Prep

**Interview Format:** Non-interactive recorded video | 30 sec think + 60 sec record per question
**Strategy:** Full scripts for memorization, aim for 60-90 seconds at natural speaking pace (~2.5-3 words/second)

**IMPORTANT:** You are NOT restricted to the resume you submitted in August. Talk about your most recent work and strongest projects. They already have your old resume—use this to update them with your current expertise and emphasize your parallel computing angle.

**KEY DIFFERENTIATOR:** Parallel computing & GPU programming expertise applies directly to financial systems (risk calculations, Monte Carlo simulations, high-frequency trading acceleration, real-time market data processing)

---

## HOW YOUR GRAPHICS/PARALLEL COMPUTING EXPERTISE APPLIES TO GOLDMAN SACHS

**Use this framing throughout your answers:**

### 1. GPU Programming → Accelerated Financial Computations

- **Your expertise**: CUDA path tracing, WebGPU rendering, parallel algorithms
- **GS application**: Risk calculations, VaR (Value at Risk) computations, portfolio optimization
- **Connection**: Same parallel computing principles—thousands of independent calculations processed simultaneously

### 2. Real-Time Rendering → Real-Time Trading Systems

- **Your expertise**: 5000+ dynamic lights at 60 FPS, clustered deferred rendering
- **GS application**: High-frequency trading, real-time market data feeds, order book processing
- **Connection**: Both require microsecond-level latency and processing thousands of updates per second

### 3. Performance Optimization Mindset → Low-Latency Infrastructure

- **Your expertise**: 3x-160x framerate improvements, NSight profiling, algorithmic optimization
- **GS application**: Optimizing execution times, reducing network latency, accelerating computations
- **Connection**: Same methodology—profile, identify bottlenecks, optimize, measure

### 4. Monte Carlo Path Tracing → Monte Carlo Financial Simulations

- **Your expertise**: Path tracing using Monte Carlo sampling, importance sampling, Russian Roulette
- **GS application**: Options pricing, derivatives valuation, risk assessment
- **Connection**: Literally the same algorithm—Monte Carlo methods for evaluating complex integrals

### 5. Parallel Data Pipelines → Market Data Processing

- **Your expertise**: eBPF processing 10,000+ TCP transitions/sec, stream compaction
- **GS application**: Processing millions of market ticks, aggregating order book data
- **Connection**: High-throughput data pipeline optimization, parallel processing of event streams

### 6. Memory Optimization → Cache-Efficient Financial Systems

- **Your expertise**: GPU memory management, material sorting for coherency, BVH spatial locality
- **GS application**: Optimizing cache hit rates in pricing engines, reducing memory bandwidth
- **Connection**: Both domains require careful attention to memory access patterns for performance

**KEY TALKING POINT:**
"Computer graphics and financial systems solve fundamentally similar problems—processing massive amounts of data in parallel with microsecond-level latency requirements. The difference is I apply these techniques to render images, while Goldman Sachs applies them to power global financial markets."

---

## 1. WALK ME THROUGH YOUR RESUME (60 seconds)

**SCRIPT (170 words, ~60 seconds):**

"I'm Tony Tian, a junior at Penn studying Computer Engineering, pursuing an accelerated master's in Computer Graphics and Game Technology. Although that might sound unusual for finance, my expertise is really in parallel computing and high-performance systems—which directly applies to Goldman Sachs' infrastructure.

I specialize in three areas. First, GPU programming and parallel algorithms. I've built Monte-carlo path tracers achieving 160 times performance improvements with parallel computing algorithms like stream compaction and bounding volume hierachy. These are same techniques that can be used to power risk calculations and trading systems.

Second, low-latency systems optimization. As a PURM Scholar, I built eBPF kernel monitoring processing 10,000 events per second, improving network throughput by 25%. That microsecond-level optimization mindset applies directly to trading infrastructure.

Third, I understand business impact. I tested features for Genshin Impact, a $4 billion platform with 60 million users, influencing $10 million in revenue.

I'm excited about Goldman Sachs because you're solving the same performance challenges I love—massively parallel, low-latency systems—but powering global financial markets instead of rendering pixels."

---

## 2. WHY GOLDMAN SACHS? WHY ENGINEERING? (60 seconds)

**SCRIPT (155 words, ~55 seconds):**

"I'm drawn to Goldman Sachs because you're solving the exact performance challenges I'm passionate about, but at unprecedented scale and impact.

What excites me is the intersection of parallel computing and financial engineering. I've specialized in GPU programming—CUDA, WebGPU, parallel algorithms. I've learned that when processing thousands of events per second with microsecond-level latency requirements, you need to think about parallelization, memory access patterns, and hardware architecture.

Goldman Sachs operates in that same space. Your risk calculations run massive parallel computations. Your trading systems require microsecond latency. Your pricing models use GPU-accelerated Monte Carlo simulations—literally the same algorithms I use for path tracing, just applied to options pricing instead of rendering.

I've also seen how engineering drives business value through my Genshin Impact work on a $4 billion platform. At Goldman Sachs, that connection is even more direct—better trading infrastructure, faster execution systems, more accurate risk models directly impact clients and markets.

This is where the hardest technical problems meet real-world financial impact."

---

## 3. TELL ME ABOUT A TIME YOU SOLVED A TOUGH PROBLEM (90 seconds)

**SCRIPT (240 words, ~85 seconds):**

"My toughest problem was building a CUDA path tracer where complex scenes rendered at 0.6 FPS—completely unusable. The Stanford Dragon model with hundreds of thousands of triangles was taking billions of ray-triangle intersection tests per frame.

This is similar to financial systems—when processing market data or running risk calculations, you need to optimize both algorithmic complexity and parallel execution.

My approach was systematic. First, I profiled with Nvidia NSight and found 95% of compute time in ray-intersection tests. You can't optimize what you don't measure. Then I researched spatial acceleration structures and decided to implement a Bounding Volume Hierarchy with Surface Area Heuristic for optimal tree construction.

The implementation required deep GPU architecture thinking. Traditional recursive tree traversal doesn't work on GPUs because recursion is expensive, so I implemented iterative stackless traversal. I added complementary optimizations: stream compaction to remove terminated rays, material sorting for memory coherency, and Russian Roulette for early path termination.

The result was dramatic—3x to 160x improvement depending on scene complexity. Stanford Dragon went from 0.6 FPS to 96 FPS.

More importantly, I learned a systematic methodology that applies everywhere: profile first, identify bottlenecks with data, optimize algorithmically for complexity, then optimize for hardware architecture. Whether you're optimizing rendering pipelines or trading systems, the approach is the same."

---

## 4. TELL ME ABOUT A CONFLICT ON A TEAM (90 seconds)

**SCRIPT (235 words, ~85 seconds):**

"During Mini Minecraft, I had a major disagreement with a teammate about terrain generation. I wanted layered Perlin noise creating five realistic biomes. He wanted simple random noise. His concern—my approach took five days versus his two days, and we only had two weeks left.

The disagreement got tense. He felt I was over-engineering and risking our deadline. I believed cutting corners on core features would hurt quality.

I realized the real issue wasn't technical—it was deadline anxiety. So I called a meeting and changed my approach.

First, I asked him to fully explain his concerns. Confirmed the deadline was the main worry, not the technical approach. Then I created visual mockups comparing both approaches side-by-side. The quality difference was obvious—layered Perlin created realistic mountains and smooth biome transitions, while random noise looked scattered.

Next, I proposed a data-driven solution. I broke down our timeline, showed we could parallelize other tasks like physics and rendering, and demonstrated we'd still finish two days early with the better approach. I also offered to own terrain generation entirely, reducing his workload.

Result: we implemented full Perlin noise, finished two days early, and he acknowledged the final result looked significantly better.

The lesson—when advocating technical decisions, back it up with data and address underlying concerns. In this case, proving we could meet the deadline was more important than arguing technical superiority."

---

## 5. TELL ME ABOUT A TIME YOU SHOWED LEADERSHIP (90 seconds)

**SCRIPT (250 words, ~90 seconds):**

"During PennOS, we were building a complete UNIX-like operating system with a team of four. Week three, we hit a critical roadblock—one teammate blocked on signal handling for three days. This was serious because both scheduler and shell components depended on signals working. Ten days to deadline, morale dropping.

I stepped up as leader with two priorities: unblock the teammate without taking over, and keep the team moving.

First, I scheduled a one-on-one and asked them to walk through their approach. Identified a conceptual misunderstanding about signal delivery timing between processes. Instead of just giving the answer, I pair-programmed for two hours, asking guiding questions so they discovered the solution themselves. Also drew architecture diagrams showing signal flow through process control blocks.

Second, I addressed team dynamics. Called a meeting and reframed the situation—not a 'blocking issue' but a learning opportunity to understand signal handling better for debugging later. Then I reorganized task dependencies. Identified work that could be parallelized—shell team could work on I/O redirection and pipeline chaining independently while we finished signals. Set up daily fifteen-minute standups to catch blockers earlier.

Result: teammate finished signal handling in two days and gained real confidence. We completed the project with 98%, implementing all features—preemptive scheduler, full signal handling, POSIX-compliant shell with job control.

The lesson: leadership isn't being the smartest person or solving everything yourself. It's empowering your team and removing blockers so everyone contributes their best work."

---

## 6. GOING BEYOND REQUIREMENTS / ABOVE AND BEYOND (90 seconds)

**SCRIPT (245 words, ~85 seconds):**

"My Linux kernel research is a great example. As a PURM Scholar with Professor Sebastian Angel, the initial goal was straightforward—use eBPF to collect TCP metrics from three kernel functions and analyze one workload, iperf3. Baseline: probe tcp_v4_rcv, tcp_connect, tcp_state_process, generate CSV output.

But I realized this had limited real-world value. Real systems don't just run iperf3—they have diverse workload patterns. I saw an opportunity to build actually useful infrastructure for the research community, so I expanded scope significantly.

First, increased coverage to five kernel functions instead of three—added congestion_control and cubic for deeper TCP insights. Second, tested multiple workload types—iperf3, Redis benchmarks, high-frequency trading simulations, HTTP traffic—to understand kernel policy performance under different conditions. Third, engineered for real performance—optimized pipeline to handle 10,000+ state transitions per second versus original spec under 1,000.

But I also wanted production-ready infrastructure. Wrote 2,000+ lines of C and Python with proper error handling, added automated visualization dashboards for quick bottleneck analysis, created comprehensive documentation. Open-sourced everything via KernMLOps repository—now used by 15+ researchers at Penn and UT Austin.

Impact exceeded expectations. Professor invited me to present at distributed systems lab, research led to 25% throughput improvements for specific workloads, building toward potential publication.

The lesson: when you see opportunity for broader impact beyond just meeting requirements, the extra effort is worth it."

---

## 7. TIME YOU CHOSE BETWEEN 2 OPTIONS - DECISION MAKING (90 seconds)

**SCRIPT (245 words, ~85 seconds):**

"In my WebGPU renderer, I faced a critical architectural decision: Forward+ or Clustered Deferred rendering for 5,000 dynamic lights in real-time.

Forward+ was safer—simpler, supports transparency, uses less memory bandwidth, one week to finish. But still performs redundant shading and is limited by overdraw.

Clustered Deferred was high-risk, high-reward—maximum performance by decoupling geometry from lighting, but significantly more complex. G-buffer architecture with multiple render targets plus sophisticated light culling. Three weeks to implement, and if it failed, no time to pivot back.

I approached this systematically. First, researched industry practice—AAA games use deferred for dense dynamic lighting. Second, analyzed algorithmic complexity. Forward+ is O(lights × fragments)—performance scales with both light count and pixel overdraw. Deferred is O(lights × pixels)—much better at thousands of lights. Third, considered requirements—spec required 5,000 lights, so performance at scale was critical.

But theory isn't enough for high-stakes decisions. I spent three days building minimal prototypes of both and measured actual performance. Data was clear—Clustered Deferred was 3.5x faster at target light count.

I chose Clustered Deferred despite implementation risk. Result validated the decision—53x improvement over naive rendering, 497 milliseconds to 9.3 milliseconds per frame at 5,000 lights.

The lesson: for critical technical decisions, prototype both options when possible. Data beats theory. Measuring actual performance reveals insights you can't predict."

---

## 8. ETHICAL SCENARIO - PERSONAL EMAIL BREACH (60 seconds)

**SCRIPT (150 words, ~55 seconds):**

"If I accidentally gave a client my personal email and they sent confidential information there, my immediate action: do NOT open or read the email. Notify my manager immediately before anything else. This is a potential compliance violation and data breach affecting client trust and firm reputation.

My thought process focuses on three things. First, transparency—immediately inform stakeholders: manager, then compliance, IT security, and legal as required. Hiding the mistake makes it worse. Second, containment—document exact timeline: when I gave wrong email, when client sent info, when I discovered it. Ask compliance whether to delete or preserve for investigation. Work with manager to inform client through proper channels. Third, prevention—follow incident response protocol, triple-check emails going forward, use only company directory auto-complete.

Key principle: compliance violations are serious. Be transparent, document everything, let appropriate teams handle remediation—don't try fixing it myself."

---

## 9. TECHNICAL - APPROACH TO SYSTEM DESIGN (60 seconds)

**Question Example:** "How would you design a real-time stock price feed system?"

**SCRIPT (155 words, ~55 seconds):**

"I'd start by clarifying requirements—how many stocks, how many concurrent users, latency requirements, can we tolerate message loss?

For architecture, four layers. First, data ingestion connecting to exchange APIs, normalizing formats. Second, message broker—Apache Kafka for high-throughput event streaming, handles millions of events per second with low latency. Third, processing layer doing real-time aggregation, filtering by user subscriptions. Fourth, delivery layer using WebSocket connections pushing updates to clients.

Key technical decisions focus on performance and scale. Pub-sub pattern where users subscribe to specific stocks rather than broadcasting everything. Batching—send updates every 100ms instead of instantly—reduces network overhead while maintaining perceived real-time performance. Caching layer using Redis for latest prices, reducing database load. Load balancing distributing WebSocket connections.

For reliability—horizontal scaling adding processing nodes as needed, Kafka replication and Redis clustering avoiding single points of failure, comprehensive monitoring tracking message lag and p99 latency. Can't optimize what you don't measure."

---

## 10. TECHNICAL - DEBUGGING APPROACH (60 seconds)

**Question Example:** "System is running slow in production. How do you debug?"

**SCRIPT (160 words, ~55 seconds):**

"My approach comes from optimizing parallel systems—systematic five-step process.

First, gather data, don't guess. Check monitoring dashboards for CPU, memory, network, disk I/O. Look at logs for errors or warnings when slowdown started. Ask what changed recently—deployment, traffic spike, configuration change?

Second, reproduce and isolate. Can I reproduce in staging? Affecting all users or specific subset? Binary search approach to isolate which component—frontend, backend, database, network?

Third, profile and measure. Critical step. In CUDA work, NSight profiling revealed 95% of compute time in ray-intersection tests. Can't optimize what you don't measure. For backend, use APM tools like DataDog, database query analysis, network tracing to identify exact bottleneck.

Fourth, form hypothesis and test. Based on data, form specific hypothesis—'database query taking five seconds due to missing index.' Test hypothesis, implement fix, measure improvement.

Finally, verify and document. Confirm fix works in production, document root cause, add monitoring to catch similar issues early. Profile first, optimize second—data-driven debugging is the only reliable approach."

---

## BACKUP STORIES - Quick Scripts

### If Asked About Specific Technical Achievement: Stream Compaction (60s)

**SCRIPT (130 words, ~45 seconds):**
"In my CUDA path tracer, I implemented stream compaction to optimize parallel efficiency. Problem: as rays terminate—hitting lights or bouncing too many times—we waste GPU threads processing nothing.

I used parallel prefix sum algorithm to compact the active ray buffer, removing terminated rays and keeping threads busy with real work. Achieved 24% to 67% performance improvement depending on scene complexity. Measured everything in NSight profiler with detailed warp occupancy and memory throughput analysis.

This same technique applies to financial systems. When processing market data or running risk simulations, you want to eliminate idle compute and maximize parallel efficiency. It's about keeping hardware fully utilized."

---

### If Asked About Learning/Growth: Mastering CUDA from Scratch (60s)

**SCRIPT (140 words, ~50 seconds):**
"Starting GPU Programming, I had zero CUDA experience. Learning curve was steep—GPU programming requires thinking completely differently than CPU code. Managing thousands of threads, memory hierarchies, avoiding divergence. Early implementations were actually slower than CPU versions—frustrating.

My approach was systematic. Worked through NVIDIA's CUDA guide cover-to-cover, focusing on hardware architecture—warps, streaming multiprocessors, memory coalescing. Profiled everything in NSight, even simple kernels, to build intuition. Studied high-performance implementations on GitHub.

Breakthrough came when I stopped thinking about individual threads and started thinking about data patterns—how 32 threads in a warp access memory together, how to eliminate divergence, maximize occupancy. By semester end, achieving near-theoretical peak performance.

Lesson: mastering complex systems requires both theoretical understanding and empirical measurement."

---

## KEY THEMES TO EMPHASIZE - PARALLEL COMPUTING FOCUS

**1. Parallel Computing is Your Differentiator:**

- CUDA, WebGPU, parallel algorithms, GPU architecture
- Monte Carlo methods (path tracing = options pricing)
- Stream processing (ray compaction = market data filtering)
- Same skills, different application domain

**2. Performance Optimization Methodology:**

- Profile first (NSight, eBPF, profiling tools)
- Identify bottlenecks with data, not guesses
- Optimize algorithmically AND for hardware
- Measure improvements quantitatively
- 3x-160x CUDA improvement, 53x WebGPU improvement, 25% TCP throughput improvement

**3. Real-Time, Low-Latency Systems:**

- 5000+ lights at 60 FPS (microsecond-level frame budgets)
- eBPF processing 10,000+ events/second
- 200ms embedded system response time
- Understand latency matters—relevant to HFT, trading systems

**4. Scale & Distributed Systems:**

- PennOS: 50+ concurrent processes, 95% CPU utilization
- Mini Minecraft: 1M+ blocks with spatial optimization
- Kernel research: multiple workload types, production-ready infrastructure
- Think about scalability, parallelism, resource management

**5. Engineering Drives Business Value:**

- Genshin Impact: $10M+ revenue features
- Kernel research: 25% throughput improvements
- WebGPU: 53x performance = better user experience
- Understand that technical decisions have business impact

**6. Self-Directed Learning & Initiative:**

- Accelerated master's in specialized field (CG&GT)
- Self-taught advanced techniques (BVH, clustered deferred)
- Open-source contributions (KernMLOps)
- Go beyond requirements consistently

---

## PRACTICE TIPS - MEMORIZATION & DELIVERY

### Memorization Strategy (2-3 days before interview):

**Day 1: Learn the scripts**

- Read each script out loud 5 times
- Focus on understanding the flow, not word-for-word memorization
- Record yourself reading, listen back

**Day 2: Practice delivery**

- Practice each question 3-5 times WITHOUT looking at script
- Use bullet points on notecard if you get stuck
- Time yourself—aim for 60-90 seconds
- Focus on sounding natural, not robotic

**Day 3: Mock interview**

- Randomize question order
- Record full mock interview on webcam
- Watch playback, note areas to improve (pacing, filler words, energy)

### Delivery Tips:

1. **Use the 30-second think time strategically**

   - First 10 seconds: Identify which story to use
   - Next 15 seconds: Mentally outline 3-4 key points
   - Last 5 seconds: Take deep breath, smile, start strong
2. **Vary your speaking pace**

   - Slow down for key technical achievements (shows confidence)
   - Speed up slightly when explaining context/background
   - Pause for 1-2 seconds between major points
3. **Always connect back to Goldman Sachs**

   - End technical stories with: "This same approach applies to [GS use case]"
   - Examples: "...just like optimizing trading systems" / "...similar to processing market data"
4. **Show energy and enthusiasm**

   - Smile when talking about projects you're passionate about
   - Lean forward slightly when describing solutions
   - Use hand gestures (keeps you animated, but don't overdo it)
5. **Technical Setup Checklist**

   - Camera at eye level (stack books under laptop if needed)
   - Well-lit room (window behind camera, or desk lamp)
   - Test audio—speak at normal volume, check for echo
   - Close all other applications to avoid notifications
   - Have water nearby (for between questions)
6. **The "Bridge" Technique**

   - If you forget part of script, have bridge phrases ready:
     - "The key insight was..."
     - "What made this challenging was..."
     - "The result demonstrated..."
   - These buy you 2-3 seconds to remember next point

### Red Flags to Avoid:

- ❌ Saying "I don't know" without attempting an answer
- ❌ Bad-mouthing teammates or previous experiences
- ❌ Getting too technical without explaining business impact
- ❌ Forgetting to smile or showing low energy
- ❌ Rambling past 90 seconds (they may cut you off)
- ❌ Reading directly from notes (obvious on video)

### Green Flags to Hit:

- ✅ Quantify everything with specific metrics
- ✅ Show enthusiasm for parallel computing and performance
- ✅ Connect your graphics expertise to financial applications
- ✅ Demonstrate systematic problem-solving (profile → optimize → measure)
- ✅ Mention business impact (revenue, throughput, user experience)
- ✅ Show humility ("learned that...", "this taught me...")

---

## PROJECT CHEAT SHEET - Quick Stats for Reference

| Project                         | Key Metric                           | Tech Stack                | Parallel Computing Connection                                      | Team        |
| ------------------------------- | ------------------------------------ | ------------------------- | ------------------------------------------------------------------ | ----------- |
| **CUDA Path Tracer**      | 3x-160x improvement, 0.6→96 FPS     | CUDA, C++, BVH            | Monte Carlo sampling, parallel ray intersection, stream compaction | Solo        |
| **WebGPU Renderer**       | 53x improvement, 497ms→9.3ms        | WebGPU, TypeScript, WGSL  | 5000 parallel light calculations, compute shaders, G-buffer        | Solo        |
| **PennOS**                | 95% CPU utilization, 50+ processes   | C, Shell, Kernel          | Preemptive scheduler, concurrent process management                | 4           |
| **Mini Minecraft**        | 1M+ blocks, 60 FPS                   | C++, OpenGL, GLSL, Qt     | Procedural generation, parallel rendering, spatial optimization    | 3           |
| **Linux Kernel Research** | 10k+ transitions/sec, 25% throughput | eBPF, C, Python           | High-throughput data pipeline, parallel event processing           | Solo + Prof |
| **Stream Compaction**     | 24-67% improvement                   | CUDA, Parallel Prefix Sum | Parallel reduction, warp efficiency optimization                   | Solo        |
| **Genshin Impact QA**     | $10M+ revenue features, 60M users    | QA Testing, Mobile        | Large-scale system testing, performance validation                 | Individual  |

**Key Numbers to Remember:**

- 3x to 160x (CUDA path tracer improvement)
- 53x (WebGPU renderer improvement)
- 95% (PennOS CPU utilization)
- 60 FPS (Mini Minecraft, real-time rendering target)
- 10,000+ (TCP transitions per second)
- 25% (throughput improvement from kernel research)
- 5,000 (dynamic lights in WebGPU renderer)
- $10M+ (Genshin Impact revenue influence)

---

## FINAL CONFIDENCE BOOSTERS

**Remember: Your Parallel Computing Expertise is RARE and VALUABLE**

Most engineering candidates don't have:

- ✅ Deep GPU programming experience (CUDA, WebGPU)
- ✅ Parallel algorithm implementation (BVH, stream compaction, Monte Carlo)
- ✅ Hardware-level optimization understanding (warps, memory coalescing)
- ✅ Quantified performance improvements (3x-160x, 53x)
- ✅ Direct connection to financial applications (Monte Carlo pricing, parallel risk calculations)

**The Goldman Sachs Connection is STRONG:**

"Computer graphics and financial systems solve fundamentally similar problems—processing massive amounts of data in parallel with microsecond-level latency requirements. The difference is I apply these techniques to render images, while Goldman Sachs applies them to power global financial markets. I'm excited to bring my parallel computing expertise to build the next generation of financial infrastructure."

**Your Story Arc:**

1. Started with graphics passion → discovered parallel computing
2. Built increasingly complex systems → learned performance optimization
3. Contributed to research → gained production systems experience
4. Pursued accelerated master's → deep technical specialization
5. Ready to apply skills → financial technology at Goldman Sachs

---

**FINAL REMINDERS:**

- GS Engineering Values: **Excellence, Innovation, Partnership, Integrity**
- GS Engineering Mission: **"We don't just make things—we make things possible"**
- Your Unique Angle: **Parallel computing expertise that directly enables financial innovation**
- Your Proof Points: **3x-160x CUDA, 53x WebGPU, 25% throughput, 10k+ events/sec**
- Your Mindset: **Profile → Identify → Optimize → Measure → Repeat**

**You've built amazing systems. You've achieved incredible performance gains. You have unique skills that Goldman Sachs needs. Be confident, be authentic, and let your passion for high-performance computing shine through.**

**Good luck! 🚀**
