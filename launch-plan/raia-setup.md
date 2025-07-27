# raia Setup

## ✅ Phase 1: RAIA SETUP — Simple Implementation Guide

**Goal:** Configure a functioning AI Agent in raia that can be tested and trained\
**Estimated Duration:** \~2–4 days\
**Who’s Involved:**

* Project Manager (PM)
* raia Agent Engineer (AE)
* Optional: Subject Matter Expert (SME)

***

### ⚙️ Step 1: Define the Agent’s Purpose

**Time:** \~2 hours\
**Owner:** PM + SME

**Checklist:**

* [ ] What role will the agent play? (e.g., Support Agent, Sales Assistant, Analyst)
* [ ] What are 2–3 primary outcomes the business wants?
* [ ] What types of conversations or tasks will the agent handle?

**Tip:** Use AI (like ChatGPT) to draft a description of the agent’s purpose in natural language.

***

### 🛠 Step 2: Create and Configure the Agent in raia

**Time:** \~4 hours\
**Owner:** AE

**Checklist:**

* [ ] Create a new agent in Launch Pad
* [ ] Name it clearly (e.g., “SupportBot - Acme Inc.”)
* [ ] Add description, version tags, and use-case tags
* [ ] Choose initial role-based skill template (chat, email, voice, etc.)
* [ ] Set up dev, test, and production environments

***

### 💬 Step 3: Define Agent Instructions + Personality

**Time:** \~4 hours\
**Owner:** AE

**Checklist:**

*   [ ] Use a prompt to generate starter instructions:

    > _“Write markdown instructions for an AI agent that acts as a customer support rep for a real estate software company…”_
* [ ] Edit the instructions to:
  * Match brand voice
  * List capabilities and limitations
  * Define how to handle errors and escalate
* [ ] Set tone (e.g., friendly, formal, expert)
* [ ] Define response formatting rules (e.g., bullet points, short sentences)

**Deliverable:** Clean, clear instructions saved in raia

***

### 🔌 Step 4: Configure Skills

**Time:** \~6–10 hours\
**Owner:** AE

**Checklist:**

* [ ] Enable core skills:
  * [ ] Chat
  * [ ] Email
  * [ ] SMS (if needed)
  * [ ] CRM Lookup / API Calls
* [ ] For each skill:
  * [ ] Configure it (e.g., email from address, Slack channel, etc.)
  * [ ] Test it in isolation
* [ ] Add one custom skill if needed (e.g., scoring, tagging, or workflow trigger)

***

### 🔐 Step 5: Set Up Access + Security

**Time:** \~2 hours\
**Owner:** AE

**Checklist:**

* [ ] Invite project collaborators in raia with correct roles (e.g., Admin, CoPilot-only)
* [ ] Configure access controls
* [ ] Validate API keys, permissions, and data handling
* [ ] Confirm audit logging is enabled

***

### 🧪 Step 6: Perform Initial Testing

**Time:** \~4 hours\
**Owner:** AE + PM

**Checklist:**

* [ ] Test agent startup and skill loading
* [ ] Validate 10 real-world test prompts
* [ ] Confirm agent responds with personality and accuracy
* [ ] Note any limitations, bugs, or unclear replies

**Deliverables:**

* Basic test results documented
* Any fixes made and confirmed

***

### 🧾 Step 7: Document and Prepare for Training

**Time:** \~2 hours\
**Owner:** PM

**Checklist:**

* [ ] Save agent setup snapshot
* [ ] Document:
  * Skills enabled
  * Agent instructions
  * Known limitations
* [ ] Prepare handoff notes for Phase 2 (Training)
* [ ] Confirm access for training team

***

Let me know if you’d like this turned into a downloadable checklist (PDF, Google Doc, Notion, or Markdown template).
