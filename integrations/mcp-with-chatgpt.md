# MCP with ChatGPT

## How to Access a raia AI Agent via MCP in ChatGPT

This guide explains how to connect and use a **raia AI Agent** in ChatGPT using **Model Context Protocol (MCP)**.

You will learn how to:

* Enable Developer Mode
* Create a Custom MCP App
* Connect your raia MCP endpoint
* Publish it to your workspace
* Access and use the agent in ChatGPT

***

### Overview

ChatGPT supports external AI agents via **Model Context Protocol (MCP)**. By adding your raia MCP endpoint as a custom app, you can securely interact with your raia AI Agent directly inside ChatGPT.

⚠️ Note: Custom MCP servers are considered advanced configuration and may introduce risk if improperly configured. Only connect trusted endpoints.

***

## Step 1: Enable Developer Mode

1. Open **ChatGPT**
2. Go to **Settings**
3. Click **Apps**
4. Select **Advanced settings**
5. Toggle **Developer mode** ON

When enabled:

* You can add unverified MCP connectors
* Memory is disabled for that chat session
* You accept responsibility for the endpoint being added



<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 8.59.01 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 8.59.24 AM.png" alt=""><figcaption></figcaption></figure>

***

## Step 2: Create a New MCP App

1. In **Settings → Apps**
2. Click **Create app**

You will see the **New App (Beta)** screen.

Fill in the following:

#### App Configuration

| Field              | What to Enter                                                        |
| ------------------ | -------------------------------------------------------------------- |
| **Name**           | `raia DIS` (or your preferred agent name)                            |
| **Description**    | Optional                                                             |
| **MCP Server URL** | Your raia MCP endpoint (e.g. `https://api.raia2.com/mcp/{agent-id}`) |
| **Authentication** | Select **No Auth** (if your endpoint does not require OAuth)         |

Example MCP URL format:

```
https://api.raia2.com/mcp/{agent-uuid}
```

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 8.59.30 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 9.02.20 AM.png" alt=""><figcaption></figcaption></figure>

***

### Step 3: Accept Risk Acknowledgment

Before creating the app, you must confirm:

> "I understand and want to continue"

This acknowledges:

* OpenAI has not reviewed the MCP server
* The endpoint could access or modify data
* You trust the MCP server being connected

Check the confirmation box and click **Create**.

***

## Step 4: Verify App Connection

After creation, you will see the app listed under:

**Settings → Apps → Enabled apps**

You should see:

* Your app name (e.g. `raia DIS`)
* A `DEV` badge (indicating developer mode)
* Connection status
* Authorization used (None if No Auth)

You can:

* Disconnect
* Delete
* Publish to workspace

***

## Step 5 (Optional): Publish to Your Workspace

If you want others in your workspace to use the raia agent:

1. Click the app
2. Click the **••• menu**
3. Select **Publish**

You will be prompted to:

* Review potential risk: Unauthorized data access
* Confirm understanding
* Optionally configure action confirmations

Click **Publish** to make it available to workspace members.

After publishing, it will appear in the **Apps Directory** for your workspace.

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 9.03.08 AM.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 9.03.15 AM.png" alt=""><figcaption></figcaption></figure>

***

## Step 6: Use the raia Agent in Chat

Once enabled:

1. Open a new ChatGPT conversation
2. Type `@`
3. Select your raia agent (e.g. `@raia DIS`)

You can now interact with your raia AI Agent directly within ChatGPT.

Example:

```
@raia DIS Get account summary for customer 12345
```

The MCP connection allows ChatGPT to:

* Send structured requests to your raia agent
* Execute defined MCP actions
* Return responses in-chat

***

## How It Works (Technical Summary)

* ChatGPT connects to your MCP endpoint via Server-Sent Events (SSE)
* The raia MCP server exposes defined actions
* ChatGPT calls those actions when prompted
* Responses are streamed back into the conversation

If Developer Mode is enabled:

* Memory is disabled
* The session does not retain long-term context

***

## Security Considerations

When connecting MCP endpoints:

✔ Only use trusted HTTPS endpoints\
✔ Restrict access where possible\
✔ Audit usage periodically\
✔ Avoid exposing sensitive actions without confirmation

When publishing to workspace:

* Limit who can access the app
* Configure action confirmations for consequential operations

***

## Troubleshooting

#### App does not appear in chat

* Confirm Developer Mode is enabled
* Verify the app is listed under Enabled Apps
* Refresh ChatGPT

#### MCP connection fails

* Verify the endpoint URL is correct
* Confirm the MCP server is reachable
* Check SSL configuration

#### Actions not triggering

* Confirm the MCP server exposes properly defined actions
* Ensure the prompt clearly references the agent using `@agent-name`

***

## Summary

By connecting your raia AI Agent via MCP in ChatGPT, you enable:

* Direct AI-agent interaction inside ChatGPT
* Action execution against raia systems
* Workspace-wide deployment (optional)
* Secure, extensible agent integration

This allows raia agents to operate seamlessly within ChatGPT’s conversational interface while maintaining control through MCP.

***

If you'd like, I can also provide:

* A shorter version for customer-facing documentation
* A more technical version for developers
* A version formatted for Notion or Confluence
