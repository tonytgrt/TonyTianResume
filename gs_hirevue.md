# Goldman Sachs Engineering Analyst - HireVue Prep

**Interview Format:** Non-interactive recorded video | 30 sec think + 60 sec record per question

**CRITICAL INSIGHT FROM RACHEL:**

- **Reviewers judge you in the first 2 sentences** - they lose patience quickly
- **Structure: ANSWER FIRST, then explain** - Not build-up to conclusion
- **For "Why GS": Talk about culture/people, not just technical challenges**
- **Sound natural and conversational**

**STRATEGY:**

- Memorize shortened scripts (45-70 sec base for non-native speaking pace)
- Put your strongest point in the first sentence
- You are NOT restricted to your August resume—talk about current work
- Emphasize parallel computing angle throughout
- **Optional sentences in [brackets]**: Include these ONLY if question allows 90 seconds instead of 60 seconds. They add technical depth but aren't required for core answer.

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

## 1. WALK ME THROUGH YOUR RESUME (60-90 seconds)

**SCRIPT (115 words base = ~60 sec | +45 words optional = ~80 sec):**

"I'm Tony Tian, a junior at Penn specializing in parallel computing and high-performance systems. [I'm also pursuing an accelerated master's in Computer Graphics and Game Technology, which gives me deep expertise in GPU architecture and rendering pipelines.] My expertise directly applies to Goldman Sachs' trading and risk infrastructure.

I've achieved massive performance improvements through GPU programming, such as 160 times speedup on CUDA path tracers using parallel algorithms like stream compaction. These same methods power financial risk calculations and Monte Carlo simulations.

I also optimize low-latency systems. As a PURM Scholar, I built eBPF tools which monitors 10,000 Linux kernel events per second, improving network throughput by 25%. That microsecond-level mindset applies to trading infrastructure.

I understand business impact as well. I tested features for Genshin Impact, a $4 billion platform with 60 million users. [I contributed to quality assurance for features generating over $10 million in revenue.]

I'm excited about Goldman Sachs because you solve the same performance challenges I love, but powering global financial markets."

---

## 2. WHY GOLDMAN SACHS? WHY ENGINEERING? (60-90 seconds)

**SCRIPT (110 words base = ~50 sec | +50 words optional = ~75 sec):**

"I'm drawn to Goldman Sachs because you're solving the hardest engineering problems at unprecedented scale, with real financial impact. The culture of excellence and innovation in your engineering division is exactly where I want to learn and contribute.

What excites me is the direct technical alignment. Your risk calculations run massive parallel computations—same techniques as my GPU work. Your trading systems require microsecond latency—same mindset as my kernel optimization that achieved 25% throughput improvements. Your pricing models use GPU-accelerated Monte Carlo simulations—literally the same algorithms I use for path tracing, just applied to options pricing. [The engineering challenges you face—processing millions of market events per second, optimizing for cache efficiency, building fault-tolerant distributed systems—are exactly the problems I'm passionate about solving.]

Plus, I have a connection to Salt Lake City through my friend Rachel, who's inspired me about GS culture and mentorship.

This is where technical excellence meets real-world impact."

---

## 3. TELL ME ABOUT A TIME YOU SOLVED A TOUGH PROBLEM (90 seconds)

**SCRIPT (155 words base = ~70 sec | +35 words optional = ~85 sec):**

"I achieved a 160x performance improvement on my CUDA path tracer—taking it from 0.6 FPS to 96 FPS. The problem was billions of ray-triangle intersection tests killing performance.

My approach: profile first, optimize second. NSight profiling showed 95% of time in ray intersections. I implemented a Bounding Volume Hierarchy with Surface Area Heuristic—a spatial acceleration structure that reduces complexity from O(n) to O(log n).

The challenge was GPU architecture. Traditional recursive tree traversal doesn't work because recursion is expensive on GPUs. So I implemented iterative stackless traversal, plus stream compaction to remove terminated rays, material sorting for memory coherency, and Russian Roulette for early termination. [Each optimization was measured independently in NSight profiler to validate the performance gain before adding the next one.]

Result: 3x to 160x improvement depending on scene complexity. [The Stanford Dragon scene went from completely unusable at 0.6 FPS to real-time interactive at 96 FPS.]

The methodology applies everywhere—whether optimizing rendering or trading systems. Profile with data, optimize algorithmically, then optimize for hardware. Can't optimize what you don't measure."

---

## 4. TELL ME ABOUT A CONFLICT ON A TEAM (90 seconds)

**SCRIPT (150 words base = ~70 sec | +30 words optional = ~85 sec):**

"I resolved a major disagreement with my Mini Minecraft teammate by addressing his underlying concern—deadline anxiety—with data, not just technical arguments.

The conflict: I wanted layered Perlin noise for realistic terrain, he wanted simple random noise. His worry—my approach took five days versus two days, with only two weeks left.

I realized it wasn't about technical merit. So I created visual mockups showing the quality difference, then broke down our timeline proving we could parallelize other tasks and still finish two days early. I offered to own terrain generation entirely, reducing his workload. [I also set up a shared project board so he could track my progress daily and see we were on schedule.]

Result: we implemented the better solution, finished two days early, and he acknowledged it looked significantly better. [The final game generated five distinct biomes with realistic mountain ranges and smooth transitions.]

The lesson—when advocating technical decisions, address underlying concerns with data. Proving we'd meet the deadline mattered more than arguing technical superiority."

---

## 5. TELL ME ABOUT A TIME YOU SHOWED LEADERSHIP (90 seconds)

**SCRIPT (155 words base = ~70 sec | +35 words optional = ~85 sec):**

"I unblocked my PennOS teammate and kept our team on track when signal handling blocked us for three days with ten days to deadline. Instead of taking over, I empowered them to solve it.

I pair-programmed for two hours, asking guiding questions until they discovered the solution themselves—a conceptual misunderstanding about signal delivery timing. Drew architecture diagrams showing signal flow through process control blocks. [The key was helping them understand how signals propagate between parent and child processes in our PCB data structure.]

Then I addressed team dynamics. Reframed this as a learning opportunity, not a blocker. Reorganized task dependencies so shell team could parallelize I/O redirection work independently. Set up daily standups to catch blockers earlier.

Result: teammate finished in two days with real confidence. We completed the project with 98%, implementing all features—preemptive scheduler, full signal handling, POSIX-compliant shell. [Our OS supported 50+ concurrent processes with 95% CPU utilization.]

The lesson: leadership means empowering your team and removing blockers, not being the smartest person in the room."

---

## 6. GOING BEYOND REQUIREMENTS / ABOVE AND BEYOND (90 seconds)

**SCRIPT (145 words base = ~65 sec | +40 words optional = ~85 sec):**

"I expanded my Linux kernel research from a basic class project to production-ready infrastructure now used by 15+ researchers, leading to 25% throughput improvements.

The baseline requirement: collect TCP metrics from three kernel functions, test one workload. I saw this had limited real-world value, so I expanded scope significantly.

I increased coverage to five kernel functions, tested multiple workloads—iperf3, Redis, high-frequency trading simulations, HTTP traffic. Engineered for real performance—10,000+ state transitions per second versus original spec under 1,000. [I optimized the eBPF code to minimize kernel overhead and built a lock-free ring buffer for high-throughput data collection.] Wrote 2,000+ lines of production-quality C and Python with automated visualization dashboards and documentation. Open-sourced everything via KernMLOps repository.

Result: professor invited me to present at distributed systems lab, building toward publication. [The research findings are now informing TCP optimization strategies for high-performance networking applications.]

The lesson: when you see opportunity for broader impact, the extra effort is worth it."

---

## 7. TIME YOU CHOSE BETWEEN 2 OPTIONS - DECISION MAKING (90 seconds)

**SCRIPT (140 words base = ~65 sec | +40 words optional = ~85 sec):**

"I chose the high-risk Clustered Deferred rendering approach over safer Forward+ rendering, achieving 53x performance improvement—from 497ms to 9.3ms per frame at 5,000 lights.

The decision: Forward+ was safer, one week to implement. Clustered Deferred was complex, three weeks, but theoretically 3.5x faster based on algorithmic complexity—O(lights × pixels) versus O(lights × fragments).

But theory wasn't enough for high-stakes decisions. I spent three days building minimal prototypes and measured actual performance. Data confirmed Clustered Deferred was 3.5x faster at our target. [I also researched industry practice and found AAA game engines use deferred rendering for exactly this scenario—dense dynamic lighting at scale.]

I chose the riskier option because data validated it. Result: 53x improvement over naive rendering, project succeeded. [The final renderer handled 5,000 lights at 60 FPS, rendering the Sponza scene with real-time performance metrics.]

The lesson: for critical technical decisions, prototype both options when possible. Data beats theory. Measure actual performance."

---

## 8. ETHICAL SCENARIO - PERSONAL EMAIL BREACH (60-90 seconds)

**SCRIPT (95 words base = ~45 sec | +35 words optional = ~65 sec):**

"My immediate action: do NOT open the email. Notify my manager immediately. This is a compliance violation affecting client trust and firm reputation.

Three priorities: First, transparency—inform manager, compliance, IT security, legal as required. Hiding makes it worse. Second, containment—document timeline, ask compliance whether to delete or preserve, inform client through proper channels. [I would write down exactly when I gave the wrong email, when the client sent information, and when I discovered the mistake.] Third, prevention—follow incident response protocol, triple-check emails, use only company directory.

Key principle: compliance violations are serious. Be transparent, document everything, let appropriate teams handle it—not me. [Taking responsibility while following proper procedures protects both the client and the firm.]"

---

## 9. TECHNICAL - APPROACH TO SYSTEM DESIGN (60-90 seconds)

**Question Example:** "How would you design a real-time stock price feed system?"

**SCRIPT (100 words base = ~45 sec | +50 words optional = ~70 sec):**

"I'd design four layers: data ingestion, message broker, processing, and delivery.

First, clarify requirements—stock count, concurrent users, latency tolerance, message loss tolerance.

Architecture: Kafka message broker for high-throughput event streaming—handles millions of events per second. [Each stock ticker becomes a Kafka topic partition for parallel processing.] Processing layer does real-time aggregation and filters by user subscriptions. WebSocket delivery layer pushes updates.

Key decisions: pub-sub pattern where users subscribe to specific stocks. Batch updates every 100ms to reduce network overhead. Redis caching for latest prices. [For redundancy, I'd deploy across multiple availability zones with automatic failover.] Horizontal scaling with Kafka replication and Redis clustering for reliability. Monitor message lag and p99 latency—can't optimize what you don't measure."

---

## 10. TECHNICAL - DEBUGGING APPROACH (60-90 seconds)

**Question Example:** "System is running slow in production. How do you debug?"

**SCRIPT (105 words base = ~50 sec | +45 words optional = ~75 sec):**

"My approach: profile first, optimize second. Systematic five-step process.

First, gather data—check monitoring for CPU, memory, network, disk I/O. Check logs. Ask what changed—deployment, traffic spike, config change?

Second, reproduce and isolate. Can I reproduce in staging? Binary search to isolate component—frontend, backend, database, network? [I'd use distributed tracing to follow requests across microservices and identify where latency is being introduced.]

Third, profile and measure. In CUDA work, NSight revealed 95% time in ray-intersection. Can't optimize what you don't measure. Use APM tools, database query analysis, network tracing.

Fourth, form hypothesis and test. [For example, if database queries are slow, run EXPLAIN to check indexes and execution plans.] Fifth, verify and document.

Data-driven debugging is the only reliable approach."

---

## BACKUP STORIES - Quick Scripts

### If Asked About Specific Technical Achievement: Stream Compaction (60-90s)

**SCRIPT (130 words base = ~60 sec | +30 words optional = ~75 sec):**
"In my CUDA path tracer, I implemented stream compaction to optimize parallel efficiency. Problem: as rays terminate—hitting lights or bouncing too many times—we waste GPU threads processing nothing.

I used parallel prefix sum algorithm to compact the active ray buffer, removing terminated rays and keeping threads busy with real work. Achieved 24% to 67% performance improvement depending on scene complexity. [The technique works by scanning the ray buffer in parallel, identifying active rays, and reorganizing memory so all active rays are contiguous.] Measured everything in NSight profiler with detailed warp occupancy and memory throughput analysis.

This same technique applies to financial systems. When processing market data or running risk simulations, you want to eliminate idle compute and maximize parallel efficiency. It's about keeping hardware fully utilized."

---

### If Asked About Learning/Growth: Mastering CUDA from Scratch (60-90s)

**SCRIPT (140 words base = ~65 sec | +30 words optional = ~80 sec):**
"Starting GPU Programming, I had zero CUDA experience. Learning curve was steep—GPU programming requires thinking completely differently than CPU code. Managing thousands of threads, memory hierarchies, avoiding divergence. Early implementations were actually slower than CPU versions—frustrating.

My approach was systematic. Worked through NVIDIA's CUDA guide cover-to-cover, focusing on hardware architecture—warps, streaming multiprocessors, memory coalescing. Profiled everything in NSight, even simple kernels, to build intuition. Studied high-performance implementations on GitHub. [I also joined CUDA forums and read research papers on GPU optimization techniques.]

Breakthrough came when I stopped thinking about individual threads and started thinking about data patterns—how 32 threads in a warp access memory together, how to eliminate divergence, maximize occupancy. By semester end, achieving near-theoretical peak performance.

Lesson: mastering complex systems requires both theoretical understanding and empirical measurement."

---

### If Asked About Onboarding New Team Member Mid-Project (60-90s)

**SCRIPT (135 words base = ~65 sec | +35 words optional = ~85 sec):**
"I'd focus on three things: getting them context quickly, making them productive fast, and integrating them socially.

First, I'd schedule a one-hour onboarding session to walk through our project architecture, current sprint goals, and where we are in the timeline. [I'd share our design docs, codebase structure, and our team's coding standards so they have references.] I'd explain what each team member owns and how we communicate—Slack channels, standups, code reviews.

Second, I'd pair-program with them on their first task. Choose something meaningful but not critical-path, so they can learn our workflows without pressure. Set them up with development environment, CI/CD access, and documentation.

Third, social integration—introduce them to the team during standup, invite them to team lunch, add them to our group chat. [In my PennOS project, when we added a fourth member mid-way, I created a shared knowledge document and paired with them for two days. They were contributing independently within a week.]

The goal is making them feel valued and productive immediately, not just welcomed."

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
