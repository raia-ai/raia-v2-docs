---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/EwGkQrKpAAj0jhmC3fkJ/launch-plan/ai-agent-skills/webhooks-skill
---

# Webhooks Skill

Here’s a full breakdown of how to **configure and set up the Webhook Skill** in raiaAI’s Launch Pad. This skill allows your AI agent to **integrate with third-party systems** (e.g., Salesforce, Zapier, CRMs, internal APIs) by **sending conversation data in real-time**.

***

<figure><img src="../.gitbook/assets/Screenshot 2025-04-17 at 10.18.29 AM.png" alt=""><figcaption></figcaption></figure>

#### 🌐 **Webhook Skill Setup Guide**

***

#### 🔧 What the Webhook Skill Does

* Sends data **automatically** from conversations to external URLs
* Common use cases:
  * Send lead data to a CRM
  * Trigger workflows in n8n, Zapier or Make
  * Log conversations in support systems

You can configure it to send data either:

* **After every message reply** (`onMessageEnd`)
* **After a thread is completed** (`onThreadEnd`)

***

#### ⚙️ **Setup Steps**

**1. Enable the Skill**

* Navigate to the **Agent → Skills tab**
* Click **“Add Skill”**, then choose **Webhook**
* Set status to **Active**

***

**2. Add a Webhook Endpoint**

You can add multiple endpoints if needed.

* **Webhook URL (Required):**\
  Paste the destination URL (e.g., your API endpoint or Zapier hook)
* **Name the Webhook:**\
  Give it a descriptive name like “Send to Salesforce” or “Lead Logger”
* **Trigger Settings:**\
  Toggle options:
  * ✅ `onMessageEnd`: Send data after every reply
  * ✅ `onThreadEnd`: Send data after thread ends (typically after 6 minutes of inactivity)

***

**3. Payload Configuration**

By default, raia sends a rich JSON payload with:

* Agent name
* User details (name, email, phone, IP)
* Message content
* Thread ID and timestamp
* Channel (chat, email, SMS, etc.)
* Source tags and scoring (if enabled)

You may be able to **customize the payload** or filter fields via functions or integrations downstream (e.g., in Zapier or your backend).

***

**4. Test Your Webhook**

* Use a tool like [Webhook.site](https://webhook.site/) or your actual integration endpoint
* Trigger a real message or thread in Copilot or Live Chat
* Confirm data is received and formatted correctly

***

**5. Monitor Delivery**

* Webhook success/failure is tracked in **thread metadata**
* Admins can view logs under “Messages” or “Threads” in **Mission Control**
* Failed attempts can be retried or debugged manually

***

#### ✅ Best Practices

| Tip                                      | Reason                                          |
| ---------------------------------------- | ----------------------------------------------- |
| Use `onMessageEnd` for real-time updates | Great for syncing CRMs or lead alerts           |
| Use `onThreadEnd` for summary syncs      | Ideal for structured data or delayed workflows  |
| Sanitize PII on your backend             | Secure handling of emails, phones, and user IDs |
| Keep webhook responses fast              | Timeouts may block data delivery                |
| Include test payloads in your dev docs   | Helps downstream teams understand the format    |

## [Webhook Setup Video](https://www.youtube.com/watch?v=2GQcKAVoBVs)

{% embed url="https://www.youtube.com/watch?v=2GQcKAVoBVs" %}
