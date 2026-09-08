# CS Student System Design Study Guide

[![Buy Me A Coffee](https://img.shields.io/badge/Buy%20Me%20A%20Coffee-ffdd00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black)](https://buymeacoffee.com/omercanyy)

> **A problem-driven system design curriculum for CS students who can code but don't know what a load balancer is.**

---

## What Is This?

Most system design resources target senior engineers preparing for staff-level interviews. They assume you already know what DNS, load balancing, and database sharding are.

**This curriculum assumes you know none of that.** It starts with "I wrote code on my laptop" and teaches you, concept by concept, how modern software systems are built, deployed, and scaled — using plain language, real analogies, and two systems you already know: **TinyURL** and **YouTube**.

It was created by a mentor for young aspiring software engineers, and co-authored with AI.

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

## Who Is This For?

- CS students who can write code but have never deployed anything
- Bootcamp grads who want to understand infrastructure
- Junior developers who nod along in architecture discussions but don't really get it
- Anyone who wants to understand how the internet actually works

## How It Works

Every chapter follows the same pattern:

1. **A problem** stated in words you already know
2. **Solution options** with pros, cons, and comparison tables
3. **A decision** — we pick one and explain why
4. **When alternatives work** — a different system where the other option would be better
5. **A diagram** — Mermaid architecture or sequence diagram showing the current system
6. **"What you should be able to say"** — one sentence proving you understood the concept

### Two Arcs, Two Systems

| Arc | System | Chapters | What You Learn |
|---|---|---|---|
| **Part 1** | TinyURL | Ch 1–18 | Cloud, serverless, databases, APIs, scaling, DNS, caching, queues, CAP theorem, security, deployment |
| **Part 2** | YouTube | Ch 19–28 | Docker, Kubernetes, threads & locks, load balancing, gRPC, WebSockets, design patterns, complexity classes |

## The Files

| File | Description |
|---|---|
| [**curriculum.md**](curriculum.md) | The full 28-chapter curriculum. Read this to learn. Upload to NotebookLM for audio summaries. |
| [**study-guide.md**](study-guide.md) | How to study. Per-chapter NotebookLM prompts, hands-on coding exercises, and an 8-week schedule. |

## How to Study

This isn't a textbook you passively read. Use three tools together:

### 1. 📖 Read the Curriculum
Read 2–3 chapters at a time. Understand the *what* and *why*.

### 2. 🎧 Listen with NotebookLM
Upload chapters to [NotebookLM](https://notebooklm.google.com) and generate audio overviews using the custom prompts in the study guide. Listen while commuting, exercising, or before bed.

### 3. 🛠️ Build with an AI Coding Assistant
Use the hands-on exercise prompts from the study guide with your favorite AI tool (ChatGPT, Claude, Copilot, Antigravity, Cursor — whatever you prefer). Don't just run the code — **read it, break it, fix it.**

> **The curriculum teaches concepts. The AI assistant gives you a lab partner. You learn by doing.**

## Suggested Schedule

| Week | Chapters | Theme |
|---|---|---|
| 1 | 1–4 | Code, cloud, compute, diagrams |
| 2 | 5–6 | Database + APIs |
| 3 | 7–8 | Infrastructure as Code + CI/CD |
| 4 | 9–11 | Scaling + DNS |
| 5 | 12–14 | Database scaling, caching, async |
| 6 | 15–18 | CAP theorem, analytics, security, deployment |
| 7 | 19–22 | Docker, Kubernetes, threads |
| 8 | 23–28 | Load balancing, gRPC, WebSockets, patterns, complexity |

## How to Know You're Ready

Pick a system you use daily — Spotify, Uber, Instagram, Slack. Sketch its architecture. Ask yourself:

- Where would you put the load balancer?
- What database would you use and why?
- What's the read-to-write ratio?
- What would you cache?
- What would you make async?

You don't need to get it right. You need to ask the right questions.

---

## Contributing

Found a mistake? Have a better analogy? Open an issue or PR. This is a living document.

## License

MIT — use it, share it, teach with it.

---

<a href="https://buymeacoffee.com/omercanyy" target="_blank"><img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" style="height: 60px !important;width: 217px !important;" ></a>
