# System Design School

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/omercanyy)

**Learn system design by building real systems — from zero infrastructure knowledge to designing scalable distributed systems.**

A free, open-source, 28-chapter curriculum that teaches system design concepts through building **TinyURL** and **YouTube** from scratch. No jargon assumed. Every concept is introduced as a solution to a real problem.

---

## What Is System Design School?

Most system design resources — like *Designing Data-Intensive Applications* or ByteByteGo — target senior engineers preparing for staff-level interviews. They assume you already know what DNS, load balancing, database sharding, and message queues are.

**System Design School assumes you know none of that.**

It starts with *"I wrote code on my laptop"* and teaches you, concept by concept, how modern software systems are built, deployed, and scaled to millions of users. You'll learn through:

- **Plain language** — no term is used before it's explained
- **Real analogies** — caching is memorizing your mom's phone number, not checking contacts every time
- **Two real systems** you already use — TinyURL (simple) and YouTube (complex)
- **Problem-driven chapters** — every concept is introduced because we hit a real problem that needs solving

Whether you're preparing for **software engineering interviews**, building your **first production system**, or just want to understand **how the internet actually works** — this is your starting point.

## Who Is This For?

- **CS students** who can write code but have never deployed anything to the cloud
- **Bootcamp grads** who want to understand infrastructure and distributed systems
- **Junior developers** who nod along in architecture discussions but don't really get it
- **Career switchers** learning software engineering and preparing for technical interviews
- **Anyone** who wants to understand how apps like Instagram, Uber, and Netflix work under the hood

## Philosophy

> **"How much do I need to learn?"** is the wrong question. Ask instead: **"How deeply do I understand what I've learned?"**

The biggest trap in studying system design is **the illusion of depth.** You read about database indexing and think *"Got it — there's a thing called an index, it makes lookups faster."* That's the surface. In an interview, someone will ask: *"Why does indexing make reads faster but writes slower? When would you NOT add an index?"* And you'll freeze.

**This curriculum is designed for multiple passes:**

| Pass | How | Goal |
|---|---|---|
| **1st** | Listen (NotebookLM audio) | Learn the vocabulary |
| **2nd** | Read + build (AI assistant) | Understand the *why* |
| **3rd** | Teach (explain out loud) | Prove you truly get it |

Each pass takes you deeper. Like reading philosophy — read Aristotle once and you get the basics. Read him every year and you discover new layers each time.

**The Surgery Rule:** You'll use AI to write code in the exercises. That's good — it lets you focus on concepts. But you cannot watch like a movie. The AI writes; you must understand **every line.** Because soon someone will say *"Design Twitter"* — and the AI won't be in the interview room with you.

## What You'll Learn

Every chapter follows the same pattern:

1. **A problem** stated in words you already know
2. **Solution options** with pros, cons, and comparison tables
3. **A decision** — we pick one and explain why
4. **When alternatives work** — a different system where the other option would be better
5. **A diagram** — Mermaid architecture or sequence diagram showing the current system
6. **"What you should be able to say"** — one sentence proving you understood the concept

### Two Arcs, Two Systems

| Arc | System | Chapters | Topics Covered |
|---|---|---|---|
| **Part 1** | **TinyURL** | Ch 1–18 | Cloud computing, serverless (AWS Lambda), databases (SQL vs NoSQL), REST APIs, HTTP, Infrastructure as Code, CI/CD, vertical & horizontal scaling, DNS & geo-routing, database sharding, caching (Redis), message queues (SQS), CAP theorem, ACID vs BASE, security & authentication, deployment strategies |
| **Part 2** | **YouTube** | Ch 19–28 | Async pipelines, Docker & containers, Kubernetes orchestration, processes, threads & locks, load balancing (ALB/NLB), CDNs, gRPC & Protocol Buffers, microservices architecture, WebSockets & real-time communication, design patterns (Factory, Strategy, Observer), canary deployments, complexity classes (P vs NP) |

## The Files

| File | What It Is | How to Use It |
|---|---|---|
| [**curriculum.md**](curriculum.md) | The full 28-chapter system design curriculum | Read it chapter by chapter. Upload to [NotebookLM](https://notebooklm.google.com) for AI-generated audio summaries and podcasts. |
| [**study-guide.md**](study-guide.md) | Companion study guide with exercises and prompts | Per-chapter NotebookLM prompts, hands-on coding exercises, trade-off scenarios, transfer challenges, depth-check questions, and an 8-week study schedule. |

## How to Study

This isn't a textbook you passively read. Combine three tools:

### 1. 📖 Read the Curriculum
Read 2–3 chapters at a time. Understand the *what* and *why* behind each design decision.

### 2. 🎧 Listen with NotebookLM
Upload chapters to [Google NotebookLM](https://notebooklm.google.com) and generate audio overviews using the custom prompts in the study guide. Listen while commuting, exercising, or before bed.

### 3. 🛠️ Build with an AI Coding Assistant
Use the hands-on exercise prompts from the study guide with any AI tool — ChatGPT, Claude, GitHub Copilot, Google Gemini, Cursor, or Windsurf. The AI writes the code; **you understand every line.**

> **The curriculum teaches concepts. The AI assistant gives you a lab partner. You learn by doing.**

## 8-Week Study Schedule

| Week | Chapters | Theme |
|---|---|---|
| 1 | 1–4 | Code, cloud, compute, diagrams |
| 2 | 5–6 | Databases + REST APIs |
| 3 | 7–8 | Infrastructure as Code + CI/CD |
| 4 | 9–11 | Scaling + DNS + going global |
| 5 | 12–14 | Database sharding, caching, async processing |
| 6 | 15–18 | CAP theorem, analytics, security, deployment |
| 7 | 19–22 | Docker, Kubernetes, threads & concurrency |
| 8 | 23–28 | Load balancing, gRPC, WebSockets, design patterns, complexity |

## How to Know You're Ready

Pick a system you use daily — Spotify, Uber, Instagram, Slack. Sketch its architecture. Ask yourself:

- Where would you put the load balancer?
- What database would you use and why?
- What's the read-to-write ratio?
- What would you cache?
- What would you make async?
- What breaks when you go global?

You don't need to get it right. You need to **ask the right questions** and **think in trade-offs.** That's what system design is.

---

## Keywords

`system design` · `system design interview` · `system design for beginners` · `learn system design` · `distributed systems` · `software architecture` · `cloud computing` · `AWS` · `database design` · `scalability` · `load balancing` · `caching` · `microservices` · `Docker` · `Kubernetes` · `REST API` · `gRPC` · `CAP theorem` · `CS interview prep` · `software engineering` · `TinyURL` · `system design curriculum`

## Contributing

Found a mistake? Have a better analogy? Open an issue or PR. This is a living document.

## License

MIT — use it, share it, teach with it.

---

<a href="https://buymeacoffee.com/omercanyy" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
