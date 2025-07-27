# AI Project Manager

## 📋 How to Build a Project Manager AI Agent in raia v2

Managing projects across teams and tools is hard. Updates get buried, teammates miss meetings, and the “source of truth” is often scattered across Jira tickets, Slack threads, and docs.

With **raia v2**, you can build a smart, always-on **Project Manager AI Agent** that:

* Summarizes meeting transcripts
* Tracks updates across tools like **Jira**, **Confluence**, and **Trello**
* Provides real-time answers to your team via **Copilot**, **Email**, or **SMS**
* Automates weekly updates and reminders
* Maintains both **shared team memory** and **personalized memory**

Let’s walk through how to build and deploy it.

***

### 🧱 Step 1: Define the Agent’s Role

Create a new Agent in **Launch Pad** and choose a role like **“Project Manager”**, or create a custom role like “Team Updates Bot” or “PM Assistant.”

Your Project Manager Agent should:

* Keep the team aligned with regular project updates
* Help team members catch up on what they missed
* Summarize meeting notes or standups
* Answer questions about progress, owners, and deadlines
* Integrate with your project management tools and documentation

***

### 🧠 Step 2: Write Smart Instructions

Use the Instructions field to guide the Agent’s behavior, tone, and responsibilities.

#### Sample Instructions:

```markdown
You are a helpful and organized AI Project Manager for the Product Team at ACME Inc.

Your job is to summarize updates from meetings, track the status of tasks from platforms like Jira or Trello, and help the team stay aligned.

Always write in a clear, concise, and neutral tone.

Summarize long threads or transcripts into bullet points. Focus on:
- Project goals
- Progress updates
- Blockers
- Next steps
- Assigned owners

If asked about a project, provide the latest known status, owner, and any relevant notes from past updates.

Use shared team memory (uploaded docs) for consistent answers. Also store individual interactions using personal memory to help follow up later.

Do not make up deadlines or estimates—refer to Jira or Trello data when possible.

If you're unsure about something, respond with:
> “I'm not seeing that in the latest updates. You may want to check with the project lead.”
```

***

### 📚 Step 3: Upload Project Docs and Shared Memory

To ensure your AI Agent provides accurate and consistent answers, upload:

* Project briefs
* Roadmaps
* Confluence meeting notes
* Retrospectives and summaries
* Team roles and responsibilities
* Jira sprint plans or Trello board exports (Markdown or JSON format)

These documents form the **shared team memory**, making the Agent a single source of truth for anyone who needs project context.

You can also enable **personal memory**, so the Agent can:

* Recall who asked what
* Follow up on previously discussed items
* Tailor updates based on individual project involvement

***

### 🔗 Step 4: Connect to Project Management Tools

Your Project Manager Agent can use **API/Webhook** integrations via **n8n** to pull and push data from your PM tools.

#### Common Integrations:

* ✅ **Jira**: Fetch tickets, owners, and statuses. Summarize epics.
* ✅ **Trello**: Monitor board changes, task comments, due dates.
* ✅ **Confluence**: Parse and summarize meeting notes or documentation.
* ✅ **Slack or Teams**: Send summary messages or respond to update requests.
* ✅ **Google Meet / Zoom**: Feed in meeting transcripts via Zapier or n8n for automated summarization.

#### Example Flow (via n8n):

1. New Jira issue comment or Trello update
2. Trigger webhook
3. AI Agent summarizes changes
4. Posts summary to Slack channel or sends email to the team

> You can even schedule weekly or daily digests automatically.

***

### ✉️ Step 5: Enable Multi-Channel Communication

Your Project Manager Agent can keep the team informed across:

#### ✅ Copilot

* Use it like ChatGPT, but trained on **your projects**
* Ask: “What’s the status of the website launch?” or “What’s blocked in Sprint 12?”

#### ✅ Email

* Agent receives and responds to update requests
* Can send daily or weekly digest emails automatically

#### ✅ SMS

* Use SMS for quick check-ins, reminders, or escalations (e.g., “What’s overdue today?”)

You can also trigger replies or summary reports based on keywords like "update," "progress," or "summary."

***

### 🔄 Step 6: Automate Regular Updates

Use the **Campaigns** feature or integrate with **n8n** to automate:

* 🗓️ Daily standup summaries
* 📅 Weekly progress emails
* ✅ Sprint review summaries
* 📤 Slack updates after meetings

Each message can be personalized with project name, owner, and most recent change logs, pulled from your connected tools.

***

### 🧩 Summary: Project Manager Agent Setup

| Step             | Task                                             |
| ---------------- | ------------------------------------------------ |
| 1. Role          | Choose or create "Project Manager" Agent         |
| 2. Instructions  | Define tone, responsibility, memory use          |
| 3. Upload Docs   | Add shared memory (briefs, sprints, updates)     |
| 4. Integrate     | Connect Jira, Trello, Confluence via API/Webhook |
| 5. Multi-Channel | Enable Copilot, Email, SMS for access            |
| 6. Automate      | Send updates and summaries daily or weekly       |

***

### 💡 Example Use Cases

| Use Case                | Trigger            | Output                     |
| ----------------------- | ------------------ | -------------------------- |
| Missed Meeting          | Manual (Copilot)   | Summarized transcript      |
| Sprint Status Update    | Scheduled (n8n)    | Email digest               |
| “What’s Next?” Question | SMS or Copilot     | Tasks by priority or owner |
| Task Escalation         | Jira status change | Slack alert via webhook    |

***

### 📌 Final Thoughts

Your Project Manager AI Agent helps you:

* Keep the team aligned
* Automate tedious reporting
* Centralize project knowledge
* Make updates accessible to everyone, anytime

Whether your team is in different time zones or just drowning in tasks, your Agent is always ready to summarize, organize, and respond.
