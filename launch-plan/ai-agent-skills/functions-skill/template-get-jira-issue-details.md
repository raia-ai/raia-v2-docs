---
description: >-
  This article provides specific instructions for configuring the Get Jira Issue
  Details function template. It assumes you have already navigated to the Add
  Function page for your agent.
---

# Template: Get Jira Issue Details

raia provides a prebuilt Function template for Jira so you can retrieve Jira ticket information without building a workflow from scratch. This template is powered by a generic n8n workflow maintained by the raia team.

#### When to use this template

Use **Get Jira Issue Details** when you want your agent to:

* recognize Jira issue keys (e.g., `QA-31`)
* fetch Jira ticket details on-demand
* summarize ticket information for the user (status, title, assignee, etc.)

#### How to add the template to an Agent

1. Go to **Agents → select an Agent → Skills**
2. Open **Functions Skill**
3. Click **Add Function**
4. Under **Choose function from a template**, select **Get Jira Issue Details**

When selected, the template will auto-fill the Function Name, Internal Name, Instructions, Webhook to Call, and Function Parameters.

#### Template Parameters (auto-filled)

This function requires a single parameter: `issue_key`.

```json
{
  "type": "object",
  "required": ["issue_key"],
  "properties": {
    "issue_key": {
      "type": "string",
      "pattern": "^[A-Z]+-\\d+$"
    }
  }
}
```

**Notes:**

* `issue_key` must look like `QA-31` (uppercase letters + hyphen + number).
* Only pass one issue key per function call.

#### Required Headers (Manual Configuration)

After selecting the template, you must configure the Jira authentication headers. Replace any placeholder values with your real Jira credentials.

| Header Name | Description                                                               |
| ----------- | ------------------------------------------------------------------------- |
| `email`     | The Atlassian/Jira user email for the account that created the API token. |
| `apikey`    | The Atlassian API token for that same user.                               |
| `domain`    | Your Jira site subdomain (the part _before_ `.atlassian.net`).            |

**How to find the Jira domain**

Your Jira domain is the part before `.atlassian.net`. **Important:** Enter only the subdomain, not the full URL.

| Full URL                           | Domain       |
| ---------------------------------- | ------------ |
| `https://northgroup.atlassian.net` | `northgroup` |
| `https://way-v2.atlassian.net`     | `way-v2`     |

#### Test It (Recommended)

After clicking **Add Function**, test the integration in **Copilot**.

**Example prompt:**

> “Can you check the details for QA-31?”

Confirm the agent successfully calls the function and returns the Jira ticket details.

#### Troubleshooting

| Error                                | Possible Causes                                                                                                                                                                                                           |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **401 / Unauthorized**               | <p>The <code>email</code> does not match the user who created the API token.<br>The <code>apikey</code> is incorrect, expired, or has been revoked.<br>The <code>domain</code> is wrong (must be the subdomain only).</p> |
| **Issue not found / empty response** | <p>The issue key does not exist.<br>The user associated with the API token does not have permission to view the issue or project.</p>                                                                                     |
