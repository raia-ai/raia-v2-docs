# AI Sales Agent

## 🤖 How to Build a Sales AI Agent in raia v2

**raia v2** makes it easy to build a powerful **Sales AI Agent** trained on your company’s unique products, services, and sales processes. Whether you're qualifying leads, sending follow-ups, or automating outreach, your AI Agent can engage prospects across **SMS, Email, and API**, and even connect to your **CRM** through tools like **n8n**.

This guide will walk you through how to build and deploy a high-performing Sales Agent step-by-step.

***

### 🧱 Step 1: Define the Agent Role and Purpose

Go to **Launch Pad** and click **Create Agent**. Choose **Sales Assistant** as the role or create a new custom role.

Your Sales Agent should be trained to:

* Ask qualifying questions
* Provide high-level product or service info
* Collect contact and intent data
* Guide leads to the next step (demo, booking, purchase)
* Update CRM or notify sales team when a lead is ready

***

### 🧠 Step 2: Write Effective Instructions

Your Instructions are the **most important part** of your Sales Agent. Here’s what to include:

#### Sample Instructions (Edit to match your company):

```markdown
You are a Sales AI Assistant for ACME Software. Your job is to qualify inbound leads and follow up with prospects who have shown interest in our products.

You should ask 2-3 qualifying questions to understand their needs. Your goal is to determine if they are a good fit for our product, then guide them to book a demo or talk to a sales rep.

Always be professional, friendly, and brief.

Do NOT discuss pricing unless the user asks. If asked, provide the link to our pricing page.

Qualifying questions you should ask:
1. What industry is your company in?
2. How many employees or users will need access?
3. What tools are you currently using for [function]?
4. What's your biggest challenge right now?

If the user seems like a qualified lead, offer to connect them to a sales rep or send a booking link.

If the user is not interested, politely close the conversation.

Never answer technical or support-related questions—direct them to support.

If at any point the user requests help from a person, respond with: “Let me connect you to a sales specialist.”
```

***

### 📚 Step 3: Add Company-Specific Knowledge

Upload or connect:

* Product one-pagers
* Feature comparisons
* FAQs
* Customer use cases
* Demo booking links
* Intro email templates

Use **Markdown or JSON** format for clean, AI-friendly training data.

***

### 🛠️ Step 4: Add Skills for Multi-Channel Outreach

Your Sales Agent can communicate across multiple channels. In the **Skills** tab, set up the ones you want to use:

#### ✅ SMS Skill

* Assign a phone number via Twilio (automated in raia)
* Customize the default welcome message
* Add fallback messaging for “STOP” or opt-outs
* Enable outgoing campaigns or 1-to-1 conversations

#### ✅ Email Skill

* Use your domain or default @raiabot.com
* Set a default subject and greeting
* Provide email signature
* Customize autoresponders or follow-ups

#### ✅ API Skill

* Enable outgoing HTTP requests (webhooks) to send lead data
* Receive incoming requests for lead updates or inquiries
* Format JSON payloads for structured responses

Each channel supports **incoming and outgoing** conversations, and all threads are stored in raia with full history.

***

### 🔗 Step 5: Integrate with CRM or Sales Workflow (Optional)

If you want your Sales Agent to:

* Pull in new leads from your CRM
* Push qualified leads back into your pipeline
* Log notes or conversation summaries into CRM

You can use **raia’s API and Webhook system** with a workflow tool like **n8n**.

#### 🔄 How It Works:

1. **Webhook Setup**
   * In raia, configure a webhook on `OnThreadEnd` or `OnMessageEnd`
   * Send lead data, score, or summary to your CRM or webhook listener
2. **n8n Integration**
   * Use n8n as your no-code automation tool
   * Receive the webhook in n8n and connect it to:
     * HubSpot
     * Salesforce
     * Pipedrive
     * Airtable
     * Google Sheets
   * You can also use it to:
     * Update lead status
     * Trigger alerts to your sales team
     * Assign tasks to reps
3. **CRM Data Sync (optional)**
   * Use n8n’s API nodes to **send lead updates back into raia**
   * Example: A CRM form gets filled → n8n triggers a new thread with the AI Agent

> Learn more at: [https://n8n.io](https://n8n.io/)

***

### 🧪 Step 6: Test in Copilot

Use **raia Copilot** to simulate a live lead interaction:

* Run through qualifying scenarios
* Confirm the AI asks the right questions
* Rate answers and refine the Instructions
* Test escalation, hand-off, or webhook response behavior

***

### 📈 Step 7: Launch and Monitor

Once your Agent is ready:

* Add it to a **Campaign** to start outbound messaging
* Embed it on your site with **Live Chat**
* Send demo links or forms from SMS and Email
* Track thread scores, user info, and engagement

***

### 🧩 Summary

| Step              | What You Do                             |
| ----------------- | --------------------------------------- |
| 1. Role & Purpose | Define what your Sales Agent should do  |
| 2. Instructions   | Guide tone, questions, and restrictions |
| 3. Upload Content | Train on sales sheets, FAQs, etc.       |
| 4. Setup Skills   | Enable SMS, Email, API                  |
| 5. Integrate CRM  | Use Webhooks + n8n for full sync        |
| 6. Test           | Simulate scenarios in Copilot           |
| 7. Launch         | Deploy to real users and campaigns      |

***

Ready to qualify leads 24/7?\
Let your Sales Agent do the talking—while your team focuses on closing.

**Need help setting up your Sales AI Agent?**\
Our team is happy to guide you through it. Just reach out.

