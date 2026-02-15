# Workflow Integration

## 🔗 Integration Options with raia : Extending AI Agents into Your Workflows

raia is built to be more than just an AI assistant—it’s designed to act as a **fully integrated teammate**, capable of plugging into your systems and workflows in real time.

While raia AI Agents work out of the box across omni-channel communication platforms like **SMS**, **Email**, **Live Chat**, and even **Voice**, many businesses want to go further. They want to use these Agents **inside workflows**, trigger them from other tools, or let them talk to CRMs, ticketing systems, or internal apps.

That’s where RAIA’s flexible **integration options** come into play.

<figure><img src="../../.gitbook/assets/agent_workflow_diagram.png" alt=""><figcaption></figcaption></figure>



***

### 🧠 Why Integrate Your AI Agent?

Even though raia Agents are ready to chat from the moment they’re launched, integration unlocks powerful new capabilities:

* Use the agent as a **step in your automation flow** (e.g., in n8n, make, etc)
* Let your CRM or helpdesk system **trigger an AI response**
* Push lead data, tickets, or summaries to a **3rd-party system**
* Allow your agent to **query your database** or **run internal logic**

Whether you're aiming for seamless customer journeys or smart internal operations, **integration makes your AI Agent more connected, useful, and valuable.**

<figure><img src="../../.gitbook/assets/zendesk_workflow_diagram.png" alt=""><figcaption></figcaption></figure>

***

### 🔧 1. raia **API** — Initiate and Control AI Agent Conversations

#### 📌 What It Does:

raia secure API lets **external applications** initiate a conversation with an AI Agent and receive a structured response back.

#### ✅ Use Cases:

* Trigger an AI Agent when a new lead fills out a form
* Route product inquiries through an AI before human review
* Run agents inside a **workflow tool like n8n or Zapier**
* Programmatically respond to support questions using an AI agent

#### 🔑 Key Capabilities:

* Start a new thread with user context
* Pass custom **context prompts** and metadata
* Retrieve the agent’s reply and use it inside your application
* Multi-channel aware: you can simulate a Live Chat, Email, or SMS conversation from the API

#### 🧠 When to Use:

Use the **API** when **you want to control the flow** or use the AI as **a service inside another system.**

***

### 🌍 2. **Webhooks** — Let the Agent Send Data to External Systems

#### 📌 What It Does:

Webhooks allow your AI Agent to **send data to other apps** when specific events occur during a conversation.

#### ✅ Use Cases:

* Push new qualified leads to your CRM
* Send summaries of completed conversations to your helpdesk
* Log interactions in tools like Notion, HubSpot, Slack, or Google Sheets
* Notify a manager or trigger an escalation when a certain keyword is used

#### 🔑 Key Triggers:

* `onMessageEnd`: sends a webhook after each AI response
* `onThreadEnd`: sends a webhook when a conversation is idle for 6+ minutes

Webhooks send **rich JSON data**, including:

* Full conversation history
* User info (name, email, phone, IP)
* Agent ID, score, and more

#### 🧠 When to Use:

Use **Webhooks** when your **external systems need to react to what the Agent is doing**—ideal for logging, alerts, data sync, or follow-up workflows.

***

### ⚙️ 3. **Functions** — Let the Agent Call Your APIs Mid-Conversation

#### 📌 What It Does:

Functions are **custom backend integrations** that your AI Agent can call **while it's chatting with a user**—on any channel (Live Chat, SMS, Email, etc.).

#### ✅ Use Cases:

* Look up order status
* Schedule an appointment
* Retrieve account balance
* Get shipping info from your ERP or database
* Create a ticket or task in a project management system

These functions are triggered based on **user prompts**, and the Agent **decides when to call them** based on your descriptions.

#### 🔑 Configuration:

* Define API endpoint, method, headers, and body structure
* Add input/output variables
* Include clear descriptions so the Agent knows **when** to use each one
* You can test and preview the function before launch

#### 🧠 When to Use:

Use **Functions** when you want your Agent to be **actionable**—not just conversational. These give your AI the power to **do things, not just say things.**

***

### 🌐 Summary: Choosing the Right Integration Path

| Integration Type | Best For                                        | Triggered By                       | Example                                      |
| ---------------- | ----------------------------------------------- | ---------------------------------- | -------------------------------------------- |
| **API**          | Using AI inside another app or workflow         | Your app or automation tool        | Trigger an agent reply from a webhook in n8n |
| **Webhook**      | Sending conversation data out to other tools    | AI Agent response or thread end    | Push leads to HubSpot                        |
| **Function**     | Letting the AI call your internal APIs mid-chat | User prompts during a conversation | Check order status from your ERP             |

***

### 🚀 The Power of Interoperability

With these options, RAIA Agents can work **within your stack**, not just on top of it. Whether you’re powering customer experiences, employee workflows, or backend operations—**you can make the Agent the brain inside your business logic**.

Combined with RAIA’s **omni-channel capabilities** (SMS, Email, Live Chat, Voice), these integrations help your team **automate faster, respond smarter, and scale without friction.**

***

#### Want to try an integration?

Check out the API docs, create a webhook in Launch Pad, or build your first Function in minutes.\
Need help? Our team can guide you through any integration—just ask.

{% embed url="https://youtu.be/Q0l4EK533Bw" %}

