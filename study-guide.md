# Study Guide: How to Use This Curriculum

> **This curriculum is not a textbook you passively read.** It's a knowledge base designed to be consumed through modern tools. You'll combine three things:
>
> 1. **The Curriculum** (this markdown) — read it to understand the *what* and *why*
> 2. **NotebookLM** — turn chapters into audio summaries and podcasts for review
> 3. **An AI Coding Assistant** — build hands-on experiments to *feel* the concepts
>
> Think of it like this: the curriculum is the lecture, NotebookLM is the study podcast, and the AI assistant is the lab partner.

---

## Setup

### NotebookLM (Audio Summaries)

1. Go to [notebooklm.google.com](https://notebooklm.google.com)
2. Create a new notebook
3. Upload the curriculum markdown as a source (you can upload the whole file or split into chapters)
4. Use the **Audio Overview** feature with a **custom prompt** (provided below per chapter) to generate focused podcast-style summaries

**Tips:**
- Upload 2-3 chapters at a time for focused summaries. Uploading all 28 at once makes the audio too broad.
- Use the custom prompts below — they tell NotebookLM exactly what to focus on and what analogies to use.
- Listen to audio while commuting, exercising, or before bed. Repetition helps concepts stick.
- After listening, try to explain the concept to someone (or to yourself out loud). If you can't, re-read the chapter.

### AI Coding Assistant (Hands-On Labs)

Use any AI coding assistant you prefer:
- **Antigravity** (Google)
- **ChatGPT** / **Claude** / **Copilot**
- **Cursor** / **Windsurf**

The exercises below give you **starter prompts** to paste into your AI assistant. The AI will generate code, explain it, and help you experiment. You'll learn by *doing*, not just reading.

**Tips:**
- Don't just run the code the AI gives you. **Read it**, **modify it**, **break it**, then **fix it**.
- Ask follow-up questions: "What happens if I change X?" / "Why did you use Y instead of Z?"
- If something doesn't make sense, paste the relevant curriculum chapter into the AI and ask it to explain in a different way.

---

## Per-Chapter Study Plan

### Ch 1: The Code

**NotebookLM Prompt:**
> Focus on Chapter 1. Explain the three URL shortening algorithms (random, hash, counter+Base62) as if I've never heard of any of them. Use a library book analogy — random is like randomly placing books on shelves, hashing is like a Dewey Decimal system, and counter is like numbering books as they arrive. Make sure to explain WHY counter + Base62 wins for this use case.

**Hands-On Exercise:**
> Paste this to your AI coding assistant:
> "Write me a Python script that implements all three URL shortening approaches (random string, MD5 hash truncated, counter + Base62). For each approach, generate 10,000 short codes and measure: (1) how many collisions occur, (2) how long it takes. Print a comparison table at the end."

**What to observe:** Watch how random collisions increase as the dataset grows. The counter approach should have zero collisions.

---

### Ch 2: What is the Cloud?

**NotebookLM Prompt:**
> Focus on Chapter 2. Explain cloud computing like I'm explaining it to my parents. Why can't we just run code on our laptop? Use the apartment-vs-house analogy. Keep it short — this is a simple concept.

**Hands-On Exercise:** No code for this one. Instead:
> Sign up for an AWS Free Tier account at [aws.amazon.com/free](https://aws.amazon.com/free). Just explore the console. Click around. See how many services exist. Don't create anything yet.

---

### Ch 3: Compute Options

**NotebookLM Prompt:**
> Focus on Chapter 3. Explain Lambda, EC2, and containers using the food delivery analogy (delivery vs meal kit vs buying a house with a kitchen). Make sure to explain WHEN each one makes sense — not just what they are. Emphasize that Lambda is perfect for simple, short-lived tasks.

**Hands-On Exercise:**
> "Create a simple AWS Lambda function using Python that takes a JSON input with a 'url' field and returns a Base62-encoded counter value. Walk me through deploying it using the AWS Console (step by step with screenshots/descriptions). Then show me how to test it."

**What to observe:** Notice how Lambda runs your code without you setting up any server. You upload code, it runs.

---

### Ch 4: UML Diagrams

**NotebookLM Prompt:**
> Focus on Chapter 4. Explain the four diagram types (system context, flowchart, sequence, class/entity) with one concrete example of each using our TinyURL system. Emphasize that sequence diagrams show WHAT HAPPENS OVER TIME and architecture diagrams show WHAT EXISTS.

**Hands-On Exercise:**
> "Using Mermaid syntax, create four different diagrams for a simple TinyURL system: (1) a system context diagram showing TinyURL as one box with users and external systems, (2) an architecture flowchart showing Lambda + DynamoDB + API Gateway, (3) a sequence diagram showing what happens when a user shortens a URL, and (4) an entity diagram showing the data model. Render each one and explain what it communicates that the others don't."

**What to observe:** Each diagram tells a different story about the same system.

---

### Ch 5: Storage

**NotebookLM Prompt:**
> Focus on Chapter 5. Explain the difference between SQL and NoSQL as if I'm choosing between a filing cabinet with strict folders (SQL) and a big bag where I toss labeled items (NoSQL). Make sure to explain what an INDEX is and why it makes reads faster but writes slower. Explain hashing as a magic shortcut that goes directly to the right drawer.

**Hands-On Exercise:**
> "Create a Python script that demonstrates the difference between indexed and non-indexed lookups. Use an in-memory SQLite database: (1) Create a table with 1 million rows, (2) Search for a specific value WITHOUT an index and time it, (3) Add an index, (4) Search again and time it, (5) Now benchmark INSERT speed with and without the index. Print a comparison showing how indexes speed up reads but slow down writes."

**What to observe:** The speed difference between indexed and non-indexed searches should be dramatic (100x+). Insert slowdown with indexes should be visible too.

---

### Ch 6: APIs & HTTP

**NotebookLM Prompt:**
> Focus on Chapter 6. Explain APIs like a restaurant menu. Cover HTTP methods as "verbs" that are suggestions, not rules. Make sure to explain: (1) what idempotency means with a real example, (2) why visiting a website is just a GET request, (3) what each status code means using real scenarios the student would encounter.

**Hands-On Exercise:**
> "Walk me through using curl (or Postman) to: (1) Make a GET request to google.com and see the raw HTML response, (2) Make a GET request to a public API like jsonplaceholder.typicode.com/posts/1 and see a JSON response, (3) Make a POST request to create a resource, (4) Explain each status code we get back. Then, help me deploy an API Gateway in front of the Lambda function we created earlier and test it with curl."

**What to observe:** A website is literally a GET request that returns text. The browser just renders it nicely.

---

### Ch 7: Infrastructure as Code

**NotebookLM Prompt:**
> Focus on Chapter 7. Explain IaC using the DoorDash ordering analogy — you describe what you want, someone else makes it. Emphasize the problems it solves: accidental deletions, onboarding new developers, reproducibility. Keep it practical.

**Hands-On Exercise:**
> "Write an AWS SAM template (template.yaml) that defines our TinyURL system: a Lambda function, a DynamoDB table, and an API Gateway. Walk me through deploying it with `sam deploy`. Then show me how a second developer would deploy their own isolated copy of the same stack."

**What to observe:** Running the same template creates identical infrastructure. Each developer gets their own stack with a different URL.

---

### Ch 8: CI/CD Basics

**NotebookLM Prompt:**
> Focus on Chapter 8. Explain CI/CD as "a robot that tests and deploys your code for you." Cover the pipeline stages and the three environments (dev, beta, prod). Keep it simple — students should understand the WHY, not the detailed YAML syntax.

**Hands-On Exercise:**
> "Create a simple GitHub Actions workflow (.github/workflows/deploy.yml) that: (1) runs on push to main, (2) runs Python tests, (3) if tests pass, deploys the SAM template to a staging environment. Explain each step of the YAML file."

---

### Ch 9: Vertical Scaling

**NotebookLM Prompt:**
> Focus on Chapter 9. Explain CPU, RAM, and disk like they're parts of a kitchen (CPU = the cook's speed, RAM = the counter space, disk = the pantry). Explain Lambda concurrency — not one big machine, but many tiny ones. Introduce race conditions with the counter example.

**Hands-On Exercise:**
> "Write a Python script that simulates a race condition. Create 100 threads that all try to increment a shared counter simultaneously WITHOUT any locking. Run it multiple times and show that the final count is inconsistent. Then fix it with a threading.Lock (mutex) and show the count is always correct."

**What to observe:** Without a lock, the counter will be wrong almost every time. With a lock, it's always correct. This is why race conditions matter.

---

### Ch 10: Horizontal Scaling & Load Balancing

**NotebookLM Prompt:**
> Focus on Chapter 10. Explain the sedan-vs-truck analogy for vertical vs horizontal scaling. Cover read replicas with our TinyURL example — create once, read millions. Explain load balancing algorithms like a host seating people at a restaurant.

**Hands-On Exercise:**
> "Write a Python simulation of three load balancing algorithms: round robin, least connections, and IP hash. Simulate 1000 requests hitting 5 servers. For each algorithm, print how many requests each server handled and whether the distribution is even."

---

### Ch 11: Going Global — DNS

**NotebookLM Prompt:**
> Focus on Chapter 11. Use the phone contacts analogy for DNS — you tap "Mom" and your phone knows the number. The internet's phonebook is DNS. Explain Route 53 geo-routing: same URL, different server based on location. Cover reverse proxies — API Gateway IS a reverse proxy.

**Hands-On Exercise:**
> "Help me set up a simple DNS experiment: (1) Use `nslookup` or `dig` to look up the IP address of google.com, facebook.com, and amazon.com. (2) Then use a VPN to switch to a European server and run the same lookups. Show me if the IP addresses change (they should for geo-routed services). (3) Explain what Route 53 does in AWS and how I would configure it for my TinyURL project."

**What to observe:** Big services return different IPs depending on where you're asking from.

---

### Ch 12: Database Scaling

**NotebookLM Prompt:**
> Focus on Chapter 12. Explain sharding like dividing a library into buildings (A-M in Building 1, N-Z in Building 2). Cover consistent hashing as a smarter way to decide which building. Explain archiving as moving old books to a warehouse. Include the counter modular arithmetic trick (3k, 3k+1, 3k+2).

**Hands-On Exercise:**
> "Write a Python script that simulates consistent hashing. Create a ring with 4 database nodes. Hash 100 keys and show which node each key maps to. Then add a 5th node and show that only ~20% of keys moved (not all of them). Compare this to naive modulo hashing where adding a node moves ~80% of keys."

---

### Ch 13: Caching

**NotebookLM Prompt:**
> Focus on Chapter 13. Explain caching as memorizing your mom's phone number. Cover cache-aside, write-through, and write-behind with real scenarios. Explain TTL and cache invalidation — "the hardest problem in computer science."

**Hands-On Exercise:**
> "Write a Python script with a simulated 'database' (a dictionary with a time.sleep(0.1) to simulate latency) and a 'cache' (another dictionary). Implement cache-aside: check cache first, on miss hit the DB and populate cache. Run 1000 lookups where 80% are for the same 10 keys (simulating viral URLs). Compare total time WITH cache vs WITHOUT cache."

**What to observe:** Caching should make the workload dramatically faster because 80% of requests hit the fast path.

---

### Ch 14: Async Processing & Queues

**NotebookLM Prompt:**
> Focus on Chapter 14. Use the restaurant ordering analogy — synchronous is waiting at the kitchen, async is ordering on an app and getting notified. Explain SQS, pub/sub, and Dead Letter Queues. Emphasize: SQS does NOT work for batching synchronous API responses.

**Hands-On Exercise:**
> "Help me create a simple SQS queue on AWS and write two Lambda functions: (1) a Producer that puts a message on the queue, (2) a Consumer that reads from the queue and writes to a DynamoDB table. Walk me through testing it and observing the async behavior — the producer returns immediately while the consumer processes later."

---

### Ch 15: CAP Theorem

**NotebookLM Prompt:**
> Focus on Chapter 15. Explain CAP theorem with the US/EU database story — what happens when the cable between them gets cut. The choice is: do you show an error (consistency) or do you show possibly stale data (availability)? Use the bank vs social media comparison. Cover ACID vs BASE simply.

**Hands-On Exercise:**
> "Create a Python simulation of the CAP theorem. Simulate two database nodes (US and EU) with a network connection between them. Simulate a write to the US node, then: (1) with the network UP, show that the EU node gets the update, (2) with the network DOWN (partition), show that the EU node either returns an error (CP mode) or returns stale data (AP mode). Let me toggle between CP and AP to see the difference."

---

### Ch 16: Analytics Dashboard

**NotebookLM Prompt:**
> Focus on Chapter 16. Explain the read-heavy vs write-heavy flip — URL redirects are reads, click tracking is writes. Cover the race condition with counters (two workers both reading 100, both writing 101 — lost a click). Explain MongoDB's primary/secondary/arbiter architecture. Emphasize that eventual consistency is PERFECT for view counts.

**Hands-On Exercise:**
> "Write a Python script that demonstrates the counter race condition: (1) Create a shared counter, (2) Spin up 50 threads that each 'click' 100 times (should total 5000), (3) Show the actual result WITHOUT atomic operations (will be less than 5000), (4) Fix it using threading.Lock or an atomic counter, (5) Show it's now exactly 5000."

---

### Ch 17: User Accounts & Security

**NotebookLM Prompt:**
> Focus on Chapter 17. Clearly distinguish hashing, encryption, and encoding — students mix these up constantly. Explain password storage with bcrypt + salt. Cover JWT as "a signed ID card." Explain the custom URL mutex/transaction problem.

**Hands-On Exercise:**
> "Write a Python script that: (1) Hashes a password with bcrypt and a salt, (2) Shows that the same password with different salts produces different hashes, (3) Verifies a password against the stored hash, (4) Creates a simple JWT token, decodes it, and shows what's inside. Use libraries like bcrypt and PyJWT."

---

### Ch 18: Deployment at Scale

**NotebookLM Prompt:**
> Focus on Chapter 18. Explain deployment waves like releasing a movie — start in one city, see if people like it, expand nationally. Cover canary deployments (the coal mine analogy), A/B testing, and feature flags. Keep it high-level.

**Hands-On Exercise:** This one is conceptual — no code needed. Instead:
> Read about how a real company does deployments. Search for "Netflix deployment pipeline" or "how Google deploys code" and summarize what you learn.

---

### Ch 19-28: YouTube Arc

**NotebookLM Prompt (upload Ch 19-28 together):**
> These chapters cover YouTube's architecture. For each chapter, explain the problem YouTube faces and how the solution differs from what we did in TinyURL. Focus on: (1) why Lambda doesn't work for video transcoding, (2) what Docker and Kubernetes actually do in plain English, (3) threads and locks with the bathroom door analogy, (4) why YouTube needs a real load balancer when TinyURL didn't, (5) gRPC vs REST for internal services.

**Hands-On Exercises for the YouTube Arc:**

| Chapter | Exercise Prompt |
|---|---|
| **Ch 20: Docker** | "Walk me through creating a simple Dockerfile for a Python script, building the image, and running it locally. Then modify the script, rebuild, and show that the container runs the updated version." |
| **Ch 21: Kubernetes** | "Help me set up Minikube (local K8s) and deploy a simple pod running an Nginx container. Then show me how to scale it to 3 replicas and simulate a pod crash to see K8s self-heal." |
| **Ch 22: Threads** | "Write a Python script that creates a deadlock between two threads (Thread A holds Lock 1 and waits for Lock 2, Thread B holds Lock 2 and waits for Lock 1). Then fix it by enforcing lock ordering." |
| **Ch 23: Load Balancing** | "Use Docker Compose to spin up 3 identical web servers and an Nginx reverse proxy that load-balances between them. Show me how requests get distributed using round-robin by printing which server handled each request." |
| **Ch 25: WebSockets** | "Create a simple WebSocket chat server in Python (using the `websockets` library) and a client that connects. Open two client terminals and show messages being pushed to both in real time." |
| **Ch 28: Complexity** | "Write a brute-force solution to the Traveling Salesman Problem for 10 cities. Time it. Then try 15 cities and show how the time explodes. Then implement a greedy heuristic and show it runs instantly with a 'good enough' answer." |

---

## Recommended Study Schedule

| Week | Chapters | Focus |
|---|---|---|
| 1 | Ch 1-4 | Code, cloud, compute, diagrams. Set up AWS Free Tier. |
| 2 | Ch 5-6 | Database + APIs. Deploy Lambda + DynamoDB + API Gateway. |
| 3 | Ch 7-8 | IaC + CI/CD. Automate your deployment. |
| 4 | Ch 9-11 | Scaling + DNS. Understand vertical vs horizontal. DNS experiments. |
| 5 | Ch 12-14 | Database scaling, caching, async. Build with Redis and SQS. |
| 6 | Ch 15-18 | CAP theorem, analytics, security, deployment. Wrap up TinyURL. |
| 7 | Ch 19-22 | Docker, Kubernetes, threads. Hands-on with containers. |
| 8 | Ch 23-28 | Load balancing, gRPC, WebSockets, patterns, complexity. |

**Each week:** Read chapters → Listen to NotebookLM audio → Do the hands-on exercises → Try to explain concepts to someone.

---

## How to Know You're Ready

After finishing, try this exercise:

> Pick a system you use daily (Spotify, Uber, Instagram, Slack). Open a blank document and sketch its architecture. Ask yourself:
> - Where would you put the load balancer?
> - What database would you use and why?
> - What's the read-to-write ratio?
> - What would you cache?
> - What would you make async?
> - What happens when the system goes global?

You don't need to get it right. You need to ask the right questions. If you can ask these questions and have opinions about the answers, you're ready.
