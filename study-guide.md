# Study Guide: How to Use This Curriculum

## Before You Start: Mindset

> **Read this section first. It will save you months of wasted effort.**

### There Is No Finish Line

Don't approach this curriculum thinking *"How much do I need to learn to be ready?"* That question has no answer. The right mindset is: **learn as much as you can, continuously.** If you land an internship after semester 1, great — you learned enough by then. If it takes until semester 3, you'll know even more. But you never stop studying.

### The Depth Trap

Here's the most common mistake: you read about database indexing, think *"OK, there's a thing called indexing, I click a button and it indexes, got it"* — and move on. You've learned the surface. But in an interview, someone will ask: *"Why does indexing make reads faster but writes slower? When would you NOT add an index?"* And you'll freeze.

**Every concept in this curriculum has layers.** The first time through, you'll understand the surface. That's fine. But you must come back and go deeper on each pass.

### The Iteration Model

Go through this curriculum **at least three times:**

| Pass | How | Goal |
|---|---|---|
| **1st Pass: Listen** | Upload to NotebookLM, generate audio overviews. Listen while commuting or exercising. | Get familiar with the vocabulary. Know what exists. |
| **2nd Pass: Read + Build** | Read each chapter carefully. Use an AI assistant to build the exercises. | Understand the *why* behind each decision. |
| **3rd Pass: Teach** | Explain each concept out loud — to a friend, a rubber duck, or yourself in the mirror. | If you can't explain it simply, you don't understand it well enough. |

Think of it like philosophy. Read Aristotle once and you'll get the basics. Read him every year for 10 years and you'll discover something new each time. System design concepts are the same — these are deep topics that people at MongoDB and Google are still working on.

### The Surgery Rule

You'll use AI assistants to write code in the exercises. That's good — it lets you focus on concepts instead of debugging syntax errors. **But you cannot watch like it's a movie.**

The AI writes the code. You must understand **every line, every comma, every bracket.** Because soon someone will ask you to make these decisions yourself — not for TinyURL, but for Twitter, Instagram, or whatever system they throw at you. If you only watched the surgery but never understood it, you can't operate.

**Concretely:** After the AI generates code, ask yourself:
- *"Why did it use this data structure?"*
- *"What happens if I change this parameter?"*
- *"What would break if I removed this line?"*

### Self-Assessment: How Deep Is Deep Enough?

Use this rubric for every chapter. Be honest with yourself.

| Level | Signal | Example (Database Indexing) |
|---|---|---|
| ❌ **Heard of it** | "There's a thing called indexing" | You can't explain what it does |
| ⚠️ **Can define it** | "Indexing makes database lookups faster" | You'd pass a flashcard quiz but fail a follow-up question |
| ✅ **Can reason about trade-offs** | "Indexing speeds up reads by creating a sorted lookup structure but slows down writes because every INSERT must also update the index. I'd index Column A (queried in 95% of requests) but not Column B (queried 2% of the time) because the write overhead isn't worth it." | You can explain *when to use it AND when NOT to*, with examples |

**Goal: ✅ for every concept.** Not ❌, not ⚠️. If you're stuck at ⚠️, do another iteration.

---

## Setup

### NotebookLM (Audio Summaries + Flashcards)

1. Go to [notebooklm.google.com](https://notebooklm.google.com)
2. Create a new notebook
3. Upload the curriculum markdown as a source (upload 2-3 chapters at a time for focused summaries)
4. Use the **Audio Overview** feature with the custom prompts below

**Tips:**
- Upload 2-3 chapters at a time. All 28 at once makes the audio too broad.
- Listen during commute, exercise, or before bed. Repetition helps.
- After listening, try to explain the concept out loud. If you can't, re-read the chapter.

**Trade-Off Flashcard Generation Prompt:**

> Generate flashcards from this content. Each flashcard should present a realistic scenario and two solution options. The answer should NOT be "pick option A." The answer should list the pros and cons of BOTH options, explain which one fits the scenario better, and then describe a different scenario where the OTHER option would win. The goal is to train trade-off thinking, not memorization.

### AI Coding Assistant (Hands-On Labs)

Use any AI coding assistant you prefer: Antigravity, ChatGPT, Claude, Copilot, Cursor, Windsurf.

**Tips:**
- Don't just run the code. **Read it, modify it, break it, fix it.**
- Ask follow-up questions: *"What happens if I change X?"*
- Remember the surgery rule: AI writes, you understand.

---

## Per-Chapter Study Plan

---

### Ch 1: The Code

**NotebookLM Prompt:**
> Focus on Chapter 1. Explain the three URL shortening algorithms (random, hash, counter+Base62) as if I've never heard of any of them. Use a library book analogy — random is like randomly placing books on shelves, hashing is like a Dewey Decimal system, and counter is like numbering books as they arrive. Explain WHY counter + Base62 wins.

**Hands-On Exercise:**
> "Write a Python script that implements all three URL shortening approaches (random string, MD5 hash truncated, counter + Base62). Generate 10,000 short codes with each and measure: (1) how many collisions occur, (2) how long it takes. Print a comparison table."

**Transfer Challenge:** You're building a unique coupon code generator for an e-commerce site. Codes must be unguessable (customers shouldn't predict the next code). Does the same algorithm choice apply? Why or why not?

**Trade-Off Scenario:** You need unique 8-character codes for a promo system. Option A: Counter + Base62 (sequential, predictable). Option B: Random string with collision check (unpredictable). Your system generates 1 million codes per day. Compare speed, uniqueness guarantees, and guessability.

**Depth Check:**
- 🟢 What is Base62 encoding?
- 🟡 Why does collision checking get slower as the dataset grows? What's the time complexity?
- 🔴 You have 3 servers generating codes simultaneously. How do you prevent two servers from using the same counter value?

---

### Ch 2: What is the Cloud?

**NotebookLM Prompt:**
> Focus on Chapter 2. Explain cloud computing like I'm explaining it to my parents. Use the apartment-vs-house analogy. Keep it short.

**Hands-On Exercise:** Sign up for [AWS Free Tier](https://aws.amazon.com/free). Explore the console. See how many services exist. Don't create anything yet.

**Transfer Challenge:** Dropbox moved most of their infrastructure OFF AWS onto their own servers in 2016. Why would a company do this? At what scale does it make sense?

**Trade-Off Scenario:** You're a 3-person startup with no DevOps experience. Option A: AWS (managed, pay-as-you-go, complex pricing). Option B: A dedicated server from Hetzner for \$50/month (cheap, simple, you manage everything). Compare for a side project vs a production app.

**Depth Check:**
- 🟢 What is cloud computing?
- 🟡 What are the three major cloud providers and why might you pick one over another?
- 🔴 Your AWS bill shows \$2,000/month. \$800 is data transfer. Why is data transfer expensive in the cloud and what can you do about it?

---

### Ch 3: Compute Options

**NotebookLM Prompt:**
> Focus on Chapter 3. Explain Lambda, EC2, and containers using the food delivery analogy. Emphasize WHEN each makes sense, not just what they are.

**Hands-On Exercise:**
> "Create an AWS Lambda function in Python that takes a JSON input with a 'url' field and returns a Base62-encoded counter value. Walk me through deploying and testing it."

**Transfer Challenge:** You're building an ML model training pipeline. Each training job takes 4 hours and needs a GPU. Lambda, containers, or EC2?

**Trade-Off Scenario:** Your function runs for 30 seconds and gets called 10 times per day. Option A: Lambda (\$0 at this scale). Option B: A t2.micro EC2 running 24/7 (~\$9/month). Now change it to 10,000 calls per day. Which is cheaper now?

**Depth Check:**
- 🟢 What is AWS Lambda?
- 🟡 What are Lambda's three key limitations (time, size, concurrency)?
- 🔴 At 1,000 concurrent Lambda invocations, each opens a database connection. You now have 1,000 connections to your database. Is this a problem? What solutions exist?

---

### Ch 4: UML Diagrams

**NotebookLM Prompt:**
> Focus on Chapter 4. Explain the four diagram types with one concrete example of each using TinyURL. Emphasize that sequence diagrams show WHAT HAPPENS OVER TIME and architecture diagrams show WHAT EXISTS.

**Hands-On Exercise:**
> "Using Mermaid syntax, create four diagrams for TinyURL: system context, architecture flowchart, sequence diagram (shorten flow), and entity diagram (data model). Explain what each communicates that the others don't."

**Transfer Challenge:** Find a tech blog post from Netflix or Uber engineering. Identify which diagram types they use. Can you understand the system from the diagrams alone?

**Trade-Off Scenario:** You need to explain to a non-technical PM why a feature is slow. Option A: Show a sequence diagram with latency numbers on each arrow. Option B: Show an architecture diagram. Which communicates the performance problem better?

**Depth Check:**
- 🟢 What is a sequence diagram?
- 🟡 When would you choose a sequence diagram vs an architecture diagram?
- 🔴 Draw a sequence diagram for what happens when you type google.com in your browser and press Enter. (Hint: DNS, TCP, HTTP, server, response, render.)

---

### Ch 5: Storage

**NotebookLM Prompt:**
> Focus on Chapter 5. Explain SQL vs NoSQL as filing cabinet with strict folders (SQL) vs a big bag of labeled items (NoSQL). Make sure to explain what an INDEX is and why it makes reads faster but writes slower.

**Hands-On Exercise:**
> "Create a Python script with an in-memory SQLite database: (1) Create a table with 1 million rows, (2) Search WITHOUT an index — time it, (3) Add an index — search again, time it, (4) Benchmark INSERT speed with and without the index. Print a comparison."

**Transfer Challenge:** Twitter stores tweets. Instagram stores photos + metadata. Uber stores ride history. For each — SQL or NoSQL? Why?

**Trade-Off Scenario:** You're building a social network with users, posts, comments, and likes — lots of relationships. Option A: DynamoDB (fast key-value, no JOINs). Option B: PostgreSQL (JOINs, ACID, slower at scale). Compare.

**Depth Check:**
- 🟢 What is database indexing?
- 🟡 Why does an index make reads faster but writes slower? What data structure does it typically use (B-tree)?
- 🔴 You have a table with 50 million rows. Column A appears in 95% of queries. Column B appears in 2%. Do you index both? What's the storage and write-speed cost of the unnecessary index?

---

### Ch 6: APIs & HTTP

**NotebookLM Prompt:**
> Focus on Chapter 6. Explain APIs like a restaurant menu. Cover HTTP methods as verbs that are conventions, not enforced rules. Make sure to explain idempotency with a real example and why visiting a website is just a GET request.

**Hands-On Exercise:**
> "Walk me through using curl to: (1) GET google.com and see raw HTML, (2) GET jsonplaceholder.typicode.com/posts/1 for JSON, (3) POST to create a resource, (4) Explain each status code we get back. Then deploy an API Gateway in front of our Lambda and test it."

**Transfer Challenge:** Open the [Stripe API docs](https://stripe.com/docs/api). Identify: what HTTP methods do they use? What status codes? Is it RESTful? What makes it a well-designed API?

**Trade-Off Scenario:** Your API creates a payment. The network drops after the server processes it but before the client gets the response. The client retries. Option A: Your POST is idempotent (checks if payment already exists). Option B: It's not (creates a duplicate charge). What happens in each case?

**Depth Check:**
- 🟢 What's the difference between GET and POST?
- 🟡 What does idempotent mean and why does it matter for unreliable networks?
- 🔴 Is our TinyURL `POST /shorten` idempotent? If I POST the same long URL twice, should I get the same short code or two different ones? What are the trade-offs of each design?

---

### Ch 7: Infrastructure as Code

**NotebookLM Prompt:**
> Focus on Chapter 7. Explain IaC using the DoorDash analogy — describe what you want, someone else makes it. Emphasize the problems it solves: accidental deletions, onboarding, reproducibility.

**Hands-On Exercise:**
> "Write an AWS SAM template (template.yaml) for TinyURL: Lambda + DynamoDB + API Gateway. Walk me through deploying it with `sam deploy`. Then show how a second developer deploys their own isolated copy."

**Transfer Challenge:** You join a company with 5 microservices, each deployed manually by clicking through the AWS console. What's the first thing you'd propose? What risks is the team currently carrying?

**Trade-Off Scenario:** Option A: Terraform (cloud-agnostic, large community, steeper learning curve). Option B: AWS SAM (AWS-specific, easier for serverless, limited to AWS). You're 100% on AWS with no plans to switch. Compare.

**Depth Check:**
- 🟢 What is Infrastructure as Code?
- 🟡 Why is clicking through the AWS console to create resources a problem at scale?
- 🔴 Two developers run the same Terraform script but one manually changed a setting in the console. Now the actual infrastructure doesn't match the code. What is this called (config drift) and how do you prevent it?

---

### Ch 8: CI/CD Basics

**NotebookLM Prompt:**
> Focus on Chapter 8. Explain CI/CD as "a robot that tests and deploys your code." Cover the pipeline stages and the three environments. Keep it simple — students should understand WHY, not YAML syntax.

**Hands-On Exercise:**
> "Create a GitHub Actions workflow that: (1) runs on push to main, (2) runs Python tests, (3) deploys the SAM template to staging if tests pass. Explain each step."

**Transfer Challenge:** Google deploys code to Gmail thousands of times a day. How do you think they avoid breaking things for billions of users? What would their pipeline look like?

**Trade-Off Scenario:** Option A: Deploy to production on every merge to main (continuous deployment). Option B: Deploy manually after QA sign-off (continuous delivery). For a banking app vs a social media app, which approach for each?

**Depth Check:**
- 🟢 What is CI/CD?
- 🟡 What's the difference between continuous delivery and continuous deployment?
- 🔴 Your CI pipeline takes 45 minutes. Developers merge 20 PRs per day. What problems does this create? How would you fix it?

---

### Ch 9: Vertical Scaling

**NotebookLM Prompt:**
> Focus on Chapter 9. Explain CPU, RAM, and disk like parts of a kitchen (CPU = cook speed, RAM = counter space, disk = pantry). Explain Lambda concurrency — not one big machine, many tiny ones. Introduce race conditions with the counter example.

**Hands-On Exercise:**
> "Write a Python script that demonstrates a race condition: 100 threads increment a shared counter simultaneously WITHOUT locking. Run it multiple times — the count will be wrong. Then fix it with threading.Lock and show it's always correct."

**Transfer Challenge:** Your PostgreSQL database is slow on queries. Before adding replicas or caching, what's the first thing you'd try? (Hint: vertical scaling of the DB instance, query optimization, or adding indexes?)

**Trade-Off Scenario:** Your Lambda is timing out at 15 seconds. Option A: Increase memory (more CPU automatically). Option B: Optimize the code. Option C: Move to a container. What order would you try these in and why?

**Depth Check:**
- 🟢 What is vertical scaling?
- 🟡 Why does vertical scaling have a ceiling? Why does cost grow non-linearly?
- 🔴 You double Lambda memory from 512MB to 1024MB. Execution time drops from 3s to 2s, not 1.5s. Why isn't the improvement linear? (Hint: not all bottlenecks are CPU/RAM.)

---

### Ch 10: Horizontal Scaling & Load Balancing

**NotebookLM Prompt:**
> Focus on Chapter 10. Explain the sedan-vs-truck analogy for vertical vs horizontal. Cover read replicas for TinyURL. Explain LB algorithms like a host seating people at a restaurant.

**Hands-On Exercise:**
> "Write a Python simulation of three load balancing algorithms: round robin, least connections, and IP hash. Simulate 1000 requests hitting 5 servers. Print the distribution for each."

**Transfer Challenge:** Uber during Friday evening rush hour — is it read-heavy or write-heavy? (Drivers updating locations = writes. Riders checking driver locations = reads.) How would the scaling strategy differ from TinyURL?

**Trade-Off Scenario:** Your app gets 100 reads per write. Option A: Add 3 read replicas (data stays fresh, adds replication lag). Option B: Add a Redis cache (faster hits, but stale data possible). Compare.

**Depth Check:**
- 🟢 What is a read replica?
- 🟡 Why do read replicas help TinyURL but might not help a write-heavy system like click tracking?
- 🔴 You have 3 read replicas in different regions. A user creates a URL and shares the link. Someone in another region clicks it 2 seconds later. What happens? Why? How long until it works?

---

### Ch 11: Going Global — DNS

**NotebookLM Prompt:**
> Focus on Chapter 11. Use the phone contacts analogy for DNS. Explain Route 53 geo-routing: same URL, different server. Cover reverse proxies — API Gateway IS one.

**Hands-On Exercise:**
> "Help me run `dig` or `nslookup` for google.com, facebook.com, and amazon.com. Then switch VPN to Europe and run again. Do the IPs change? Explain why."

**Transfer Challenge:** How does facebook.com route you to a nearby server? Is it the same mechanism we're using (DNS geo-routing)? Are there alternatives (anycast, CDN-based routing)?

**Trade-Off Scenario:** Option A: One global stack in US-East, serve everyone from there. Option B: Three regional stacks with Route 53 geo-routing. Your traffic is 90% US. Compare cost vs latency for the 10% international users.

**Depth Check:**
- 🟢 What is DNS?
- 🟡 How does Route 53 decide which IP address to return based on the requester's location?
- 🔴 A user uses a VPN set to the US but is physically in Japan. Which TinyURL stack serves them? Why? Is this a problem?

---

### Ch 12: Database Scaling

**NotebookLM Prompt:**
> Focus on Chapter 12. Explain sharding like dividing a library into buildings. Cover consistent hashing as a smarter way to decide which building. Include the counter modular arithmetic trick.

**Hands-On Exercise:**
> "Write a Python script that simulates consistent hashing: 4 nodes on a ring, hash 100 keys, show distribution. Add a 5th node — show only ~20% of keys moved. Compare to naive modulo where ~80% move."

**Transfer Challenge:** WhatsApp stores billions of messages. How would you shard the messages table — by user ID, by conversation ID, or by date? What are the trade-offs of each?

**Trade-Off Scenario:** Option A: Hash-based sharding (hash(key) % N — even distribution). Option B: Range-based sharding (A-M on shard 1, N-Z on shard 2 — easier range queries). For our short codes, which is better? What about for a time-series database?

**Depth Check:**
- 🟢 What is database sharding?
- 🟡 Why does adding a shard with naive modulo hashing cause massive data migration?
- 🔴 Explain consistent hashing — how the ring works, why only ~1/N of keys move when adding a node, and what "virtual nodes" solve.

---

### Ch 13: Caching

**NotebookLM Prompt:**
> Focus on Chapter 13. Explain caching as memorizing your mom's phone number. Cover cache-aside, write-through, write-behind. Explain TTL and cache invalidation.

**Hands-On Exercise:**
> "Write a Python script with a simulated 'database' (dictionary + 0.1s sleep for latency) and a 'cache' (dictionary). Implement cache-aside. Run 1000 lookups where 80% are for the same 10 keys. Compare total time WITH vs WITHOUT cache."

**Transfer Challenge:** Would you cache Uber driver locations? They change every few seconds. What caching strategy would you use? Why is this harder than caching TinyURL redirects?

**Trade-Off Scenario:** Option A: Cache-aside with 1-hour TTL. Option B: Write-through with no TTL. Your data changes every 5 minutes. Compare freshness, complexity, and cache size.

**Depth Check:**
- 🟢 What is caching?
- 🟡 Why is cache invalidation "the hardest problem in computer science"?
- 🔴 Your cache has a 95% hit rate. You increase the TTL from 1 hour to 24 hours. Hit rate stays 95% but users complain about stale data. How do you handle invalidation for data that changes unpredictably?

---

### Ch 14: Async Processing & Queues

**NotebookLM Prompt:**
> Focus on Chapter 14. Use the restaurant analogy — synchronous = waiting at the kitchen, async = ordering on an app. Explain SQS, pub/sub, and DLQ. Emphasize: SQS doesn't work for batching sync API responses.

**Hands-On Exercise:**
> "Create an SQS queue on AWS. Write two Lambda functions: a Producer that sends a message and a Consumer that reads it and writes to DynamoDB. Test the async behavior."

**Transfer Challenge:** When you order on Amazon, you get a confirmation email instantly but the package ships hours later. What pattern is this? What queue sits between the order and the warehouse?

**Trade-Off Scenario:** A user uploads a profile photo. Option A: Resize synchronously (user waits 3s for the response). Option B: Return immediately, resize async, show a placeholder until done. For a chat app where the photo appears in messages — which approach?

**Depth Check:**
- 🟢 What is a message queue?
- 🟡 Why can't we batch synchronous API responses through SQS?
- 🔴 Your SQS consumer reads a message, starts processing, then crashes. What happens to the message? What is "visibility timeout" and why does it matter?

---

### Ch 15: CAP Theorem

**NotebookLM Prompt:**
> Focus on Chapter 15. Explain CAP with the US/EU database story. Cover ACID vs BASE simply. The bank vs TinyURL comparison.

**Hands-On Exercise:**
> "Simulate the CAP theorem in Python: two database nodes, a network connection. Write to US, read from EU with network up (consistent) and down (partition). Show CP mode (error) vs AP mode (stale data)."

**Transfer Challenge:** Is your bank account balance eventually consistent or strongly consistent? What about Instagram likes? Twitter follower counts? How can you tell by using the product?

**Trade-Off Scenario:** EU replica is 3 seconds behind US primary. Option A: Block EU reads until synced (CP — correct but slow). Option B: Serve stale data (AP — fast but potentially wrong). For a medical records system, which? For a social media feed, which?

**Depth Check:**
- 🟢 What is the CAP theorem?
- 🟡 Why can't a distributed system guarantee all three (Consistency, Availability, Partition Tolerance)?
- 🔴 DynamoDB offers both eventually consistent reads (cheap) and strongly consistent reads (2x cost). When would you pay the premium? What about a mix within the same app?

---

### Ch 16: Analytics Dashboard

**NotebookLM Prompt:**
> Focus on Chapter 16. Explain the read-heavy vs write-heavy flip. Cover the counter race condition. Explain MongoDB primary/secondary/arbiter. Emphasize that eventual consistency is perfect for view counts.

**Hands-On Exercise:**
> "Create a race condition demo: shared counter, 50 threads × 100 clicks = should be 5000. Show the wrong result WITHOUT atomics, then fix with threading.Lock. Show it hits exactly 5000."

**Transfer Challenge:** YouTube view counts, Twitter like counts, Instagram follower counts — are these strongly consistent or eventually consistent? How can you tell as a user?

**Trade-Off Scenario:** Tracking click counts. Option A: Atomic increment in DynamoDB per click (accurate, expensive at scale). Option B: Batch clicks in memory, flush to DB every 60 seconds (cheaper, lose up to 60s of data on crash). Compare.

**Depth Check:**
- 🟢 What is a race condition?
- 🟡 How does an atomic increment prevent two threads from both writing count=101?
- 🔴 You're using atomic increments but have 3 regional write replicas. US says count=500, EU says count=503. Which is correct? How do they reconcile?

---

### Ch 17: User Accounts & Security

**NotebookLM Prompt:**
> Focus on Chapter 17. Clearly distinguish hashing, encryption, and encoding. Explain password storage with bcrypt + salt. Cover JWT as "a signed ID card." Explain the custom URL mutex.

**Hands-On Exercise:**
> "Write a Python script that: (1) Hashes a password with bcrypt + salt, (2) Shows same password + different salt = different hash, (3) Verifies a password against stored hash, (4) Creates and decodes a JWT. Use bcrypt and PyJWT."

**Transfer Challenge:** How does "Login with Google" work on a third-party app? Does the app ever see your Google password? What's happening under the hood (OAuth2 flow)?

**Trade-Off Scenario:** Option A: Session-based auth (server stores session state, uses cookies). Option B: JWT (stateless, token-based). You have 5 microservices that need to verify the user. Compare.

**Depth Check:**
- 🟢 What is hashing?
- 🟡 Why do we add a random salt before hashing a password?
- 🔴 Two users have the same password. Without salt, they have the same hash in your database. Why is this a security problem? How does salt fix it?

---

### Ch 18: Deployment at Scale

**NotebookLM Prompt:**
> Focus on Chapter 18. Explain deployment waves like releasing a movie in one city first. Cover canary deployments, A/B testing, and feature flags.

**Hands-On Exercise:** No code — read about how [Netflix deploys code](https://netflixtechblog.com/) or search "how Google deploys code at scale." Summarize what you learn.

**Transfer Challenge:** Netflix deploys thousands of times per day to 200 million users. What safeguards do you think they have? How is their pipeline different from our simple beta → prod?

**Trade-Off Scenario:** You're deploying a database migration that changes a column type. Option A: Feature flag the new code path (both old and new code coexist). Option B: Blue-green deployment (switch all traffic at once). Compare risk and complexity.

**Depth Check:**
- 🟢 What is a canary deployment?
- 🟡 How do you decide when to promote a canary from 5% to 100%? What metrics do you watch?
- 🔴 Your canary shows a 0.1% higher error rate than stable. Is that statistically significant? How do you decide whether to roll back or continue?

---

### Ch 19-28: YouTube Arc

**NotebookLM Prompt (upload all YouTube chapters together):**
> These chapters cover YouTube's architecture. For each, explain the problem YouTube faces and how the solution differs from TinyURL. Focus on: (1) why Lambda can't do video transcoding, (2) Docker and Kubernetes in plain English, (3) threads and locks with the bathroom door analogy, (4) why YouTube needs a real load balancer, (5) gRPC vs REST for internal services.

**Hands-On Exercises:**

| Chapter | Exercise |
|---|---|
| **Ch 20: Docker** | "Walk me through creating a Dockerfile for a Python script, building the image, and running it. Then modify the script, rebuild, and show the container runs the updated version." |
| **Ch 21: K8s** | "Set up Minikube locally. Deploy an Nginx pod. Scale to 3 replicas. Kill a pod and watch K8s restart it." |
| **Ch 22: Threads** | "Write a deadlock in Python: Thread A holds Lock 1, waits for Lock 2. Thread B holds Lock 2, waits for Lock 1. Then fix it with lock ordering." |
| **Ch 23: LB** | "Use Docker Compose to run 3 web servers + Nginx reverse proxy load balancing. Show which server handles each request." |
| **Ch 25: WebSockets** | "Create a WebSocket chat server in Python (websockets library). Open two clients. Show real-time message broadcasting." |
| **Ch 28: Complexity** | "Brute-force TSP for 10 cities. Time it. Try 15 cities — watch the time explode. Implement a greedy heuristic — instant, 'good enough' result." |

**Transfer Challenges for YouTube Arc:**

| Chapter | Challenge |
|---|---|
| **Ch 19: Upload Pipeline** | Spotify processes uploaded podcasts (noise reduction, normalization, multi-bitrate). How similar is their pipeline to YouTube's? |
| **Ch 20: Docker** | You need to deploy a Python app and a Node.js app to the same server. Without containers, what problems arise? |
| **Ch 21: K8s** | AWS Fargate handles scaling automatically. When would you choose Kubernetes over Fargate despite the extra complexity? |
| **Ch 22: Threads** | Node.js is single-threaded but handles thousands of concurrent connections. How? (Hint: event loop, async I/O.) |
| **Ch 23: LB** | A gaming server needs all packets from one player to go to the same server. Which LB algorithm? Why? |
| **Ch 24: gRPC** | Why does the YouTube mobile app use REST to talk to YouTube's servers, but YouTube's internal services use gRPC? |
| **Ch 25: WebSockets** | Slack shows a typing indicator when someone is typing. REST or WebSocket? What about email — would Gmail use WebSockets? |
| **Ch 26: Patterns** | You have 3 payment providers (Stripe, PayPal, Square). Which design pattern lets you swap them without changing business logic? |
| **Ch 27: Deployment** | A/B testing says the new UI increases watch time by 4% but decreases ad clicks by 2%. Do you ship it? Who makes that call? |
| **Ch 28: Complexity** | Your PM asks you to find the "optimal" ad placement across 50 ad slots and 1000 advertisers. Is this P or NP? What do you tell the PM? |

**Trade-Off Scenarios for YouTube Arc:**

| Chapter | Scenario |
|---|---|
| **Ch 20** | Option A: One fat container with all dependencies. Option B: Separate containers for FFmpeg and your code, communicating via shared volume. Compare. |
| **Ch 21** | Option A: K8s auto-scaling based on CPU. Option B: Auto-scaling based on SQS queue depth. For transcoding workers, which metric is better? |
| **Ch 22** | Option A: 8 threads sharing one process (shared memory, needs locks). Option B: 8 separate processes (isolated memory, no locks needed). Compare for CPU-bound transcoding. |
| **Ch 23** | Option A: Layer 4 NLB (fast, no HTTP inspection). Option B: Layer 7 ALB (slower, can route by URL path). For routing `/api/videos` and `/api/comments` to different server groups, which? |
| **Ch 24** | Option A: All internal services use REST (simpler, everyone knows it). Option B: gRPC internally, REST externally (faster, more complex). At 100 internal requests/sec vs 1 million/sec, does the answer change? |

**Depth Checks for YouTube Arc:**

| Chapter | 🟢 Surface | 🟡 Understanding | 🔴 Application |
|---|---|---|---|
| **Ch 20** | What is Docker? | What's the difference between an image and a container? | Your Docker image is 2GB. Deployment takes 10 minutes. How do you reduce image size? (multi-stage builds, Alpine base) |
| **Ch 21** | What is Kubernetes? | What happens when a pod crashes? | You have a K8s deployment with 10 replicas and a rolling update. 3 new pods crash on startup. What happens? Does K8s keep rolling or stop? |
| **Ch 22** | What is a mutex? | What is a deadlock and how do you prevent it? | You have a thread pool of 8 threads and 100 videos to transcode. What happens if one video is corrupted and its thread hangs forever? How do you handle it? |
| **Ch 23** | What is a load balancer? | What's the difference between Layer 4 and Layer 7? | You're load balancing WebSocket connections. Round robin assigns connections at connect time but some connections last 2 hours. Is the load balanced over time? |
| **Ch 25** | What are WebSockets? | When would you use WebSockets vs HTTP polling? | 500,000 concurrent WebSocket connections to one chat server. Each uses ~10KB of memory. How much RAM is that? What do you do when one server can't hold them all? |
| **Ch 28** | What is NP-Hard? | Why can't you brute-force TSP for 30 cities? | Your PM says "just use more servers." Can parallelism solve an NP-Hard problem? Why or why not? |

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

**Each week:** Read → Listen (NotebookLM) → Build (AI assistant) → Transfer (apply to another system) → Test yourself (depth checks)

**After completing all 8 weeks:** Start over. Second pass. You'll be amazed at how much more you understand.

---

## How to Know You're Ready

After finishing (at least two passes), try this:

> Pick a system you use daily (Spotify, Uber, Instagram, Slack). Open a blank document and sketch its architecture. Ask yourself:
> - Where would you put the load balancer?
> - What database would you use and why?
> - What's the read-to-write ratio?
> - What would you cache?
> - What would you make async?
> - What breaks when you go global?

**The real test:** Explain your design decisions out loud. If you sound confident and can justify every choice with trade-offs — you're ready. If you hesitate or can't explain *why* — do another pass.

Remember: an interviewer doesn't expect you to be right. They expect you to **think in trade-offs.** Every answer should sound like: *"Option A gives us X but costs us Y. Option B gives us Y but costs us X. For this system, I'd choose A because..."*

That's the voice of someone who understands system design.
