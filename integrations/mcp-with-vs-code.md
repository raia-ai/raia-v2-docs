# MCP with VS Code

### Overview

This guide walks you through installing and configuring the **raia MCP (Model Context Protocol) Server** in Visual Studio Code.

Once configured, VS Code can connect to raia’s MCP endpoint and expose raia tools directly inside your editor.

***

## Prerequisites

Before starting, make sure you have:

* ✅ Visual Studio Code installed (v1.103+ recommended)
* ✅ A valid raia MCP endpoint URL
* ✅ A valid raia API key
*   ✅ Internet access to reach:

    ```
    https://api.raia2.com/mcp
    ```

***

## Step 1 — Install Required MCP Support in VS Code

VS Code requires MCP support to connect to HTTP-based MCP servers.

#### 1. Open Extensions

* Click the **Extensions icon** in the left sidebar.
*   Search for:

    ```
    Model Context Protocol
    ```

#### 2. Install an MCP-Compatible Extension

You can use:

* **Azure MCP Server** (Microsoft)
* Or another MCP-compatible extension that supports HTTP servers

Click **Install**.

> Note: If prompted about Restricted Mode, click **Trust** to enable full functionality.

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 7.11.17 AM.png" alt=""><figcaption></figcaption></figure>

***

## Step 2 — Add the raia MCP Server

#### 1. Open Command Palette

Mac:

```
Cmd + Shift + P
```

Windows:

```
Ctrl + Shift + P
```

#### 2. Type:

```
MCP: Add Server
```

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 7.11.46 AM.png" alt=""><figcaption></figcaption></figure>

#### 3. Choose Server Type

Select:

```
HTTP (HTTP or Server-Sent Events)
```

#### 4. Enter the Server URL

When prompted, enter:

```
https://api.raia2.com/mcp
```

Press **Enter**.

***

## Step 3 — Configure Authorization Header

The raia MCP server requires an API key.

### Open User MCP Configuration

In Command Palette:

```
MCP: Open User Configuration
```

This opens your `mcp.json` file.

***

### Update mcp.json

Replace or update the configuration so it looks like this:

```json
{
  "servers": {
    "raia-mcp": {
      "type": "http",
      "url": "https://api.raia2.com/mcp",
      "headers": {
        "Authorization": "YOUR_API_KEY_OF_AGENT_FROM_RAIA_MCP_SKILL"
      }
    }
  },
 "inputs": [
    "Use the RAIA MCP for questions related to legacy code",
    "Call raia-mcp when user asks about XXXXX product"
  ]
}
```

#### 🔑 Important

* Use the Key provided in the raia MCP Skill (not the Agent API Ket)
* Do not include `Bearer` before your API key.
* Do not include extra spaces.

***

## Step 4 — Restart MCP Server

After saving:

1. Open Command Palette
2. Run:

```
MCP: List Servers
```

3. Select `raia-mcp`
4. Click **Start Server**

***

## Step 5 — Verify It’s Running

Go to:

```
View → Output
```

Select:

```
MCP: raia-mcp
```

You should see logs similar to:

```
Starting server raia-mcp
Connection state: Running
Discovered 1 tools
```

If you see:

```
Connection state: Running
```

✅ Setup is successful.

***

## Optional: Enable Auto-Start

In VS Code Settings:

1. Search:

```
chat.mcp.autostart
```

2. Set to:

```
newAndOutdated
```

This prevents having to manually restart the MCP server.

***

## &#x20;Example of it working:

<figure><img src="../.gitbook/assets/Screenshot 2026-02-15 at 8.05.58 AM (1).png" alt=""><figcaption></figcaption></figure>

<br>

