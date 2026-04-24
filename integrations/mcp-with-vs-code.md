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
    	},
		"NAME OF AGENT": {
			"url": "https://api.raia2.com/mcp",
			"type": "http"
		}
	},
	"inputs": []
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

\
Common Error:&#x20;

```log
2026-02-15 09:46:45.378 [info] Starting server raia-mcp
2026-02-15 09:46:45.378 [info] Connection state: Starting
2026-02-15 09:46:45.378 [info] Starting server from LocalWebWorker extension host
2026-02-15 09:46:45.381 [info] Connection state: Running
2026-02-15 09:46:45.560 [info] Connection state: Error Error sending message to https://api.raia2.com/mcp: TypeError: Failed to fetch
```

This error happens due to CORS. To fix follow these instructions:<br>

Put these instructions into the AI Chat in VS Code

````
# RAIA MCP Setup Guide for Cloud VS Code

Complete step-by-step instructions to set up the RAIA MCP server in cloud-based VS Code (VS Code Web, Codespaces, or cloud IDE).

---

## Step 1: Locate Your Configuration Files

In cloud VS Code, settings are typically stored in the cloud profile. You need to find or create:

```
~/.config/Code/User/mcp.json
```

Or if using VS Code Web/Codespaces:
```
.vscode/mcp.json
```

### How to Check

Open the **Integrated Terminal** in cloud VS Code:
- Press `Ctrl + ~` (backtick)
- Run: `ls ~/.config/Code/User/` or `ls .vscode/`

---

## Step 2: Create/Update mcp.json

### Option A: Using VS Code UI

1. Press `Cmd/Ctrl + K Cmd/Ctrl + O` to open a folder
2. Create a new file: `.vscode/mcp.json`
3. Paste this configuration:

```jsonc
{
  "servers": {
    "raia-mcp": {
      "type": "http",
      "url": "https://api.raia2.com/mcp",
      "headers": {
        "Authorization": "5980e9f1-47b2-49c1-b166-3c157afdaaa5"
      }
    }
  },
  "inputs": [
    "Use the RAIA MCP for researching code for Quantum",
    "Call raia-mcp when user asks about how the legacy code works"
  ]
}
```

4. **Save** the file (`Cmd/Ctrl + S`)

### Option B: Using Terminal

Open the integrated terminal and run:

```bash
# Create the directory if it doesn't exist
mkdir -p ~/.config/Code/User

# Create the mcp.json file
cat > ~/.config/Code/User/mcp.json << 'EOF'
{
  "servers": {
    "raia-mcp": {
      "type": "http",
      "url": "https://api.raia2.com/mcp",
      "headers": {
        "Authorization": "5980e9f1-47b2-49c1-b166-3c157afdaaa5"
      }
    }
  },
  "inputs": [
    "Use the RAIA MCP for researching code for Quantum",
    "Call raia-mcp when user asks about how the legacy code works"
  ]
}
EOF
```

---

## Step 3: Enable MCP in Settings

### Option A: Via VS Code Settings UI

1. Press `Cmd/Ctrl + ,` to open Settings
2. Search for: `chat.mcp.autostart`
3. Toggle the checkbox **ON**
4. Search for: `chat.mcp.enabled`
5. Toggle the checkbox **ON**

### Option B: Via settings.json

1. Press `Cmd/Ctrl + Shift + P`
2. Search for: `Preferences: Open Settings (JSON)`
3. Add these lines (or update if they exist):

```json
{
  "chat.mcp.autostart": true,
  "chat.mcp.enabled": true
}
```

4. **Save** the file

---

## Step 4: Verify the Configuration

### Check File Exists

In the integrated terminal, run:

```bash
# For cloud VS Code with cloud profile
cat ~/.config/Code/User/mcp.json

# OR for local .vscode folder
cat .vscode/mcp.json
```

You should see your RAIA MCP configuration printed.

### Test Network Connection

Before reloading VS Code, verify the MCP server is reachable:

```bash
curl -s -X POST "https://api.raia2.com/mcp" \
  -H "Authorization: 5980e9f1-47b2-49c1-b166-3c157afdaaa5" \
  -H "Content-Type: application/json" \
  -H "Accept: application/json, text/event-stream" \
  -d '{"jsonrpc": "2.0", "method": "tools/list", "id": 1}' | head -20
```

**Expected output**: Should show a response starting with `event: message` or `data:` (not an error).

---

## Step 5: Reload VS Code

### Option A: Reload Window

1. Press `Cmd/Ctrl + Shift + P`
2. Search for: `Developer: Reload Window`
3. Press Enter

### Option B: Close and Reopen

1. Close cloud VS Code completely
2. Re-open it in your browser

---

## Step 6: Test the MCP Connection

Once reloaded, open VS Code Chat:

1. Click the **Chat icon** in the left sidebar (or press `Cmd/Ctrl + Shift + I`)
2. Type this test message:

```
Query RAIA MCP: What is the Quantum system?
```

**Expected result**: You should receive a detailed response about your Quantum dealership system.

---

## Troubleshooting

### Issue: "MCP server not found" or connection fails

**Solution 1**: Verify the config file path
```bash
# Check where VS Code looks for config in cloud
echo $HOME
ls -la ~/.config/Code/User/mcp.json
```

**Solution 2**: Verify settings are enabled
```bash
# Check settings.json
cat ~/.config/Code/User/settings.json | grep chat.mcp
```

Should show:
```json
"chat.mcp.autostart": true,
"chat.mcp.enabled": true
```

### Issue: "Unauthorized" or 403 error

The auth token may be invalid or expired. Verify:
```bash
# Check the token in mcp.json
cat ~/.config/Code/User/mcp.json | grep Authorization
```

Should show:
```
"Authorization": "5980e9f1-47b2-49c1-b166-3c157afdaaa5"
```

If token is outdated, update it in `mcp.json`.

### Issue: Network timeout (curl command times out)

The cloud environment may have firewall restrictions. Try:
```bash
# Test basic connectivity
ping -c 1 api.raia2.com
curl -I https://api.raia2.com/mcp
```

If no response, contact your cloud provider's admin about outbound HTTPS access.

### Issue: "406 Not Acceptable" error

This means VS Code's MCP Client isn't sending the right headers. Verify you're running:
- VS Code version 1.90+
- Latest settings applied (reload window)

---

## Advanced: Manual MCP Client (if auto-connect fails)

If the built-in MCP Client isn't working, you can manually query using Python:

```bash
# Install dependencies
pip install requests

# Create a query script
cat > query_mcp.py << 'EOF'
import requests
import json

url = "https://api.raia2.com/mcp"
headers = {
    "Authorization": "5980e9f1-47b2-49c1-b166-3c157afdaaa5",
    "Content-Type": "application/json",
    "Accept": "application/json, text/event-stream"
}
payload = {
    "jsonrpc": "2.0",
    "method": "tools/call",
    "params": {
        "name": "get-any-info-about-Code_Agent_-_Quantum",
        "arguments": {"prompt": "What is Quantum?"}
    },
    "id": 1
}

response = requests.post(url, json=payload, headers=headers, verify=False, stream=True)
for line in response.iter_lines():
    if line:
        print(line.decode('utf-8'))
EOF

# Run it
python3 query_mcp.py
```

---

## Summary

| Step | Action | Verification |
|------|--------|--------------|
| 1 | Create `~/.config/Code/User/mcp.json` | `cat ~/.config/Code/User/mcp.json` |
| 2 | Add RAIA MCP config | File contains `"raia-mcp"` entry |
| 3 | Enable in settings | `chat.mcp.autostart: true` |
| 4 | Reload VS Code | Window reloads successfully |
| 5 | Test with Chat | Query returns Quantum info |

Once working, you can ask any question and I'll automatically query the RAIA MCP for Quantum code insights!

````
