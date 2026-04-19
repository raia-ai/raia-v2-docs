---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/EwGkQrKpAAj0jhmC3fkJ/launch-plan/ai-training-guide
---

# AI Training

## 🧠 How RAIA Trains Custom AI Agents with Your Knowledge

At RAIA, we believe great AI isn’t just smart—it’s _informed_. That’s why our platform is built to train each AI Agent with the **right combination of general intelligence and business-specific knowledge**, resulting in conversations that feel accurate, helpful, and personalized.

Here's how RAIA makes that happen.

***

### 🚀 Built on OpenAI, Enhanced by You

Every RAIA Agent starts with a powerful foundation: OpenAI’s industry-leading large language models. These models offer exceptional reasoning, language understanding, and general knowledge—out of the box.

But here’s the magic: RAIA lets you **layer on your internal knowledge** and **shape your AI's behavior** with tools that make it uniquely yours.

<figure><img src="../.gitbook/assets/The 4-Layer Training System - visual selection (1).png" alt=""><figcaption></figcaption></figure>

***

### 🧱 The 4-Layer Training System

To ensure RAIA Agents deliver high-quality, context-aware responses, we use a **4-layer architecture** to control what they know and how they respond:

***

#### 1. **General AI Model**

<figure><img src="../.gitbook/assets/Screenshot 2025-04-17 at 12.04.02 PM.png" alt="" width="375"><figcaption></figcaption></figure>

_Powered by OpenAI_\
This is the base layer. It allows your Agent to answer general questions, use logic, and write in natural language. But on its own, it doesn’t know your company, your customers, or your specific processes.

***

#### 2. **Vector Store (Custom Knowledge Layer)**

<figure><img src="../.gitbook/assets/Screenshot 2025-04-17 at 12.03.03 PM.png" alt="" width="344"><figcaption></figcaption></figure>

_Your documents, embedded into your Agent_

This is where RAIA becomes _your_ AI. You can upload documents like:

* SOPs, product manuals, policies, FAQs
* PDFs, DOCs, TXT files
* Training decks, meeting notes—even website pages via scraping

RAIA automatically converts this content into **semantic embeddings** and stores it in a **vector store**. This allows the AI to retrieve relevant answers based on **your exact wording, tone, and expertise**.

**How to upload training content:**

1. Go to the **Agent → Train** tab
2. Upload files (max 20 docs, up to 500MB total)
3. Optionally tag or title each document for organization
4. RAIA syncs and indexes them instantly

🧠 _Want dynamic updates?_ You can enable integrations with cloud storage like Google Drive for automatic syncing.

***

#### 3. **Instructional Prompt (Agent Identity & Behavior)**

<figure><img src="../.gitbook/assets/Screenshot 2025-04-17 at 12.01.34 PM.png" alt="" width="375"><figcaption></figcaption></figure>

_Controls how the Agent thinks and responds_

This is the "personality and mission" layer of your AI Agent. You define how it behaves, what its boundaries are, and how it solves problems.

Example instructional prompts:

* “You are a helpful assistant trained to support customer success reps at a B2B SaaS company.”
* “Always escalate billing issues to a human agent.”
* “Use a casual, supportive tone—like you're a smart friend helping out.”



***

#### 4. **Context Prompt (Personalized to the User)**

_Fine-tune each conversation with user-specific context_

This is where **true personalization** happens. The Context Prompt lets you inject dynamic, session-based info such as:

* The user’s name, plan level, or purchase history
* Support ticket metadata
* CRM or internal system data

This prompt is passed at runtime via:

* **API** (in the body of a POST request to the conversation endpoint)
* **Live Chat SDK** (embedded context when launching the widget)

💡 This means your AI Agent can greet users by name, tailor answers to their account, or change tone depending on user type—all in real time. You can define this during agent creation in Launch Pad or pass it dynamically via the API or Live Chat SDK for specific use cases.

***

### 👨‍🏫 Train Through Conversation: Human Feedback via Copilot

Training doesn't stop at setup. RAIA’s **Copilot** experience lets you test your AI Agent in real conversations and improve it continuously with human feedback.

<figure><img src="../.gitbook/assets/Screenshot 2025-04-17 at 12.04.35 PM.png" alt="" width="375"><figcaption></figcaption></figure>

#### Copilot Feedback Tools:

* **Rate Responses** with 👍 or 👎
* **Leave Comments** explaining what was right or wrong
* **Suggest Better Answers** directly in the UI
* **Flag Threads** for future training use

Admins can also **add specific threads to training memory**, improving the Agent’s responses over time—no code needed.

***

### 🔁 Continuous Improvement with Layered Intelligence

By combining these four layers—**General AI Model**, **Vector Store**, **Instructional Prompts**, and **Context Prompts**—RAIA ensures your AI Agent is:

✅ Smart (thanks to OpenAI)\
✅ Aligned with your company’s voice and rules\
✅ Informed by your internal documentation\
✅ Personalized to each user interaction

It’s everything you’d expect from a well-trained employee—only faster, more scalable, and always available.

***

#### Ready to train your AI Agent?

Head to **Launch Pad** to create your agent, upload documents, define your prompts, and watch your AI workforce grow smarter with every interaction.

{% embed url="https://youtu.be/6DC2tmRaWHs" %}

