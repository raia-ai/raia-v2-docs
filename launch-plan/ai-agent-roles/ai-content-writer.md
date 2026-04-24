# AI Content Writer

## ✍️ How to Build an AI Content Writer in raia v2

Want to scale content creation without adding headcount?\
With **raia v2**, you can build an **AI Content Writer** that understands your brand, follows your tone, and produces high-quality content like:

* 📰 Blog articles
* 📧 Marketing emails
* 📢 Social media captions
* 📄 Sales copy and landing pages
* 📝 Internal docs or newsletters

Whether you want to collaborate with the AI inside **Copilot** or fully automate your workflows using **Zapier** or **n8n**, raia gives you complete control over how and what your Agent creates.

***

### 🧱 Step 1: Define the Role of the Content Agent

Start by creating a new Agent in **Launch Pad**. Choose a role like **“AI Content Writer”** or create a custom one like “BlogBot,” “Copy Assistant,” or “Newsletter Writer.”

This Agent’s job is to:

* Generate written content on demand
* Match your brand voice and audience
* Follow structural or stylistic rules you define
* Adapt to different content types (blogs, emails, headlines, etc.)
* Be triggered either manually (via Copilot) or automatically (via API/Webhook)

***

### 🧠 Step 2: Write Instructional Prompts for Style, Voice, and Structure

Your Instructions are the key to guiding the **writing style**, **tone**, and **formatting** of your content. Think of it as the creative brief your AI follows every time it writes.

#### Sample Instructions for a Content Agent:

```markdown
You are a professional marketing copywriter for ACME Tech, a SaaS platform that helps small businesses automate their customer support.

You write content that is clear, confident, and slightly witty. You avoid jargon and focus on delivering helpful, practical insights.

You may be asked to write blogs, marketing emails, ad copy, or social media content. Follow these tone guidelines:
- Voice: Friendly, authoritative, helpful
- Target audience: Tech-savvy professionals, small business owners
- Always include a call-to-action when appropriate

When writing blog content:
- Use short paragraphs
- Include headings and bullet points when useful
- Start with a hook, end with a takeaway

Never fabricate statistics. If data is not provided, keep statements general. Do not use "As an AI..." phrasing.

If you’re unsure, ask for clarification before proceeding.
```

***

### 📚 Step 3: Upload Brand Guidelines or Writing Samples

Help your Agent learn how your team writes by uploading:

* Brand tone/voice documents
* Past blog articles
* Email campaign examples
* Headline formulas
* Social post templates

Use **Markdown** or **clean JSON** formatting where possible to preserve structure.

> 🔁 These documents are indexed into the **Vector Store**, so your Agent can reference them when generating new content.

***

### 🛠️ Step 4: Choose How to Use the Agent

#### ✅ Option 1: Use **Copilot** for Manual Writing

* Chat with your Content Agent in a clean UI
* Request a blog post on a topic
* Ask for 3 subject line variations
* Edit, give feedback, and refine content in real-time

Use cases:

* Content team wants quick drafts or inspiration
* Non-writers need help crafting professional copy

#### ✅ Option 2: Use **Automation via Zapier or n8n**

Trigger content creation automatically with structured inputs:

**Examples:**

* A new **Airtable row** is added with a blog title → Agent generates full post
* A **form submission** from marketing provides product info → Agent creates a launch email
* A **Slack command** triggers a summary post from a pasted URL

#### How It Works:

1. **Webhook or API trigger** starts the Agent
2. Provide inputs like:
   * Content type
   * Topic or brief
   * Keywords or desired tone
3. The Agent returns generated content via webhook
4. Output is sent to email, CMS, Google Doc, Airtable, or anywhere you need

**n8n** and **Zapier** make it easy to connect this workflow without writing code.

***

### 🔄 Optional: Add Skills for Email or API Delivery

You can also enable your Content Agent to:

* **Send content drafts via Email** to your team or clients
* **Return results via API** to your website or content management system

Use the **Email skill** for delivery and the **API skill** for headless content generation.

***

### 🧪 Step 5: Test and Tune

Test your Agent in Copilot before launching:

* Try different content requests
* Review formatting and tone
* Give thumbs-up/down feedback to improve responses
* Update Instructions as you learn what works best

> 🎯 Tip: Train your Agent to handle multiple formats with if/then guidance (e.g., “If asked for an email, include a subject line and preview text”).

***

### 📈 Use Cases for the AI Content Writer

| Use Case          | Trigger Method     | Output Example                   |
| ----------------- | ------------------ | -------------------------------- |
| Blog generation   | Copilot / Zapier   | 800-word article with headings   |
| Email campaigns   | n8n / Form trigger | Subject + body + CTA             |
| Social content    | Copilot            | 3 post variations per topic      |
| Product updates   | Zapier + CRM       | Email or doc summarizing changes |
| Landing page copy | Copilot            | Headline + subhead + value props |

***

### 🧩 Summary: How to Launch an AI Content Writer

| Step                     | Action                                               |
| ------------------------ | ---------------------------------------------------- |
| 1. Define Role           | Create "Content Writer" Agent                        |
| 2. Write Instructions    | Guide tone, format, purpose                          |
| 3. Train with Samples    | Upload writing guidelines                            |
| 4. Choose Interface      | Copilot for real-time / Zapier or n8n for automation |
| 5. Add Skills (Optional) | Enable Email or API for delivery                     |
| 6. Test                  | Review content and tune instructions                 |
| 7. Launch                | Automate or collaborate with your Agent              |

***

### 📌 Final Thoughts

Creating content takes time. raia’s AI Content Writer helps you scale your creativity without sacrificing quality. Whether you’re writing your next blog post or automating drip campaigns, this Agent is your always-available creative partner

