# AI Support Agent

## 🛟 How to Build a Support AI Agent in raia v2

If your team is overwhelmed with repetitive support tickets or you're looking to provide 24/7 help to customers without expanding your headcount, a **Support AI Agent** in **raia v2** is the perfect solution.

You can train your Agent on your existing help content, deploy it as a **Live Chat** on your website, receive **support questions via email**, and even integrate it with your existing **knowledge base and support systems** through **APIs and webhooks**.

This guide shows you how to build, train, and launch a Support Agent step by step.

***

### 🧱 Step 1: Set the Agent’s Role and Focus

Start in **Launch Pad**, and create a new Agent with the role **Support Assistant** or a custom role such as “Customer Care Bot” or “Tier 1 Support.”

Your Support Agent’s purpose:

* Answer common support questions (FAQs, how-tos, troubleshooting)
* Reduce support volume by resolving simple issues autonomously
* Collect essential context before handing off to a human if needed
* Support customers via **Live Chat** and **Email**
* Integrate with knowledge bases and ticketing tools (like HelpScout, Zendesk, or Freshdesk)

***

### 🧠 Step 2: Write Effective Instructions

Instructions help define the Agent’s behavior, tone, responsibilities, and limits.

#### Sample Instructions for a Support Agent:

```markdown
You are a friendly and helpful Support Assistant for ACME Software. Your role is to assist customers with product questions, usage issues, and troubleshooting steps.

You should reference the company knowledge base when possible, and provide clear answers using simple language. Ask clarifying questions when needed.

If a customer asks about an issue you can't answer, or if the situation appears complex or urgent, escalate the conversation to a human support agent.

Never give legal, financial, or medical advice. Avoid discussing topics outside of ACME Software.

If a user requests a human agent, responds with:  
“Let me connect you to our support team—please hold one moment.”

Ask for:
- Customer email (if needed)
- A description of the issue
- Product area or feature involved
```

***

### 📚 Step 3: Upload Training Content

Train your Agent on your existing support materials:

* Help center articles
* Troubleshooting guides
* Onboarding instructions
* Feature FAQs
* Refund and billing policies

> 🔁 Best practice: Consolidate this into a single **Markdown** or **JSON** knowledge base that can be updated regularly.

You can also connect a webhook or API to dynamically access your knowledge base (see below).

***

### 🛠️ Step 4: Add Support Skills

In the **Skills** tab, configure how your Support Agent will interact with customers.

#### ✅ Live Chat Skill

* Embed your Agent on your website with a customizable widget
* Configure a welcome message (e.g., “Hi! I’m here to help with any product questions.”)
* Adjust branding and colors
* Add geographic or IP restrictions if needed

#### ✅ Email Skill

* Assign a support email (e.g., `support@yourdomain.com`)
* Set autoresponder and fallback messages
* Incoming emails trigger threads the AI Agent can respond to
* Include custom signature, headers, or disclaimers

#### ✅ API Skill

* Enable your Agent to send structured replies or trigger workflows via outgoing webhook
* Useful for connecting to internal systems or updating support tickets

***

### 🔗 Step 5: Connect to Knowledge Base or Support Tools via API/Webhooks

Want your Agent to:

* Search your knowledge base in real time?
* Create or update support tickets in Zendesk, HelpScout, or Freshdesk?
* Post summaries to Slack or Teams?

You can do this with **raia’s webhook + API integration**, often using a no-code automation tool like **n8n**.

#### Integration Examples:

**1. Search Knowledge Base in Real-Time**

* Use a webhook to query your documentation API
* Return summaries or article links in the Agent’s responses

**2. Create Support Tickets Automatically**

* When a user requests escalation or types “help,” send a webhook to n8n
* n8n creates a support ticket in your platform, attaches the transcript, and notifies your team

**3. Log Agent Responses or User Feedback**

* Push every resolved thread or low-rated thread into your CRM or support dashboard for QA

#### Setup Steps:

* In raia, add a Webhook trigger on `OnMessageEnd` or `OnThreadEnd`
* Use n8n to parse the payload and send it to your support system
* You can also push conversation summaries, tags, customer info, or feedback

***

### 🧪 Step 6: Test in Copilot

Before going live, use **raia Copilot** to:

* Simulate support conversations
* Test if the Agent retrieves accurate answers
* Try edge cases and escalation scenarios
* Provide feedback using thumbs up/down and improve the Instructions

***

### 🚀 Step 7: Launch Your Agent

Once tested:

* Embed the **Live Chat widget** on your website
* Turn on the **Support Email** channel
* Add the Agent to an **internal support portal** or intranet
* Monitor engagement, feedback, and conversation scores in **Mission Control**

***

### 🧩 Summary: Support Agent Setup

| Step                  | Task                                         |
| --------------------- | -------------------------------------------- |
| 1. Define Role        | Support Agent, Tier 1 Assistant              |
| 2. Write Instructions | Define tone, duties, escalation rules        |
| 3. Upload Content     | Help docs, policies, guides                  |
| 4. Add Skills         | Live Chat, Email, API/Webhook                |
| 5. Integrate Tools    | Use n8n for knowledge base + ticketing       |
| 6. Test               | Use Copilot to refine and simulate           |
| 7. Launch             | Embed chat, route email, monitor performance |

***

### 🔄 Bonus Tip: Keep the Agent Fresh

Update your knowledge base regularly and re-train your Agent with new documentation, feature launches, or updated policies. A smart support Agent gets smarter over time.

