---
description: Raia Reasoning Agent VS Code Extension
---

# VS Code + Agent

## Raia Reasoning Agent VS Code Extension

Installation & Usage Guide

This guide explains how to install and run the Raia Reasoning Agent VS Code extension using the hardcoded configuration version.

{% file src="../.gitbook/assets/raia-vscode-extension 2.zip" %}



***

### ✅ 1. Download & Extract

1. Download the extension ZIP file.
2. Extract it anywhere on your system.
3. You should see:

```
package.json
tsconfig.json
.vscode/launch.json
src/extension.ts
.gitignore
README.md
INSTALL.md
```

***

### ✅ 2. Open the Extension Project in VS Code

1. Open **Visual Studio Code**.
2. Go to **File → Open Folder…**
3. Choose the extracted extension folder.

***

### ✅ 3. Install Dependencies

In the VS Code terminal, run:

```bash
npm install
```

This installs all required dependencies (TypeScript, VS Code types, etc.).

***

### ✅ 4. Configure Your Raia Agent API Key

Open:

```
src/extension.ts
```

At the very top, update your configuration:

```ts
const RAIA_API_URL = "https://api.raia2.com";
const RAIA_AGENT_KEY = "{put your Agent API key}";
const RAIA_PROMPT_PREFIX =
  "You are a Raia reasoning AI Agent helping modernize and improve this codebase.";
const POLL_INTERVAL_MS = 1000;
const MAX_WAIT_MS = 120000;
```

Replace:

```ts
"{put your Agent API key}"
```

with your real **Agent-Secret-Key** from Raia.

Example:

```ts
const RAIA_AGENT_KEY = "sk-raia-xxxxxxxxxxxxxxxxxxxxx";
```

No VS Code settings required — this version is fully hardcoded for reliability.

***

### ✅ 5. Build the Extension

Compile the TypeScript:

```bash
npm run compile
```

If successful, an `out/` directory will be generated.

***

### ✅ 6. Run the Extension

In VS Code, press:

```
F5
```

This launches a new window called:

#### **Extension Development Host**

Your Raia extension is now active in this sandboxed VS Code session.

***

### ✅ 7. Using the Raia Reasoning Agent Command

In the **Extension Development Host** window:

1. Open any code file.
2. Select the code you want to send to Raia\
   &#xNAN;_(if nothing is selected, the whole file is used)_
3. Press:

```
Cmd/Ctrl + Shift + P
```

4. Run the command:

```
Raia: Ask Reasoning Agent
```

5. Enter an instruction for the agent, such as:

* “Refactor this function.”
* “Rewrite using async/await.”
* “Identify potential bugs.”
* “Optimize this component.”

The extension will:

* Submit the request to `/external/prompts/async`
* Poll `/external/prompts/{id}/response-on`
* Display the final reasoning response in a new tab

***

### 🧩 Additional Notes

* This extension uses **hardcoded configuration** for maximum reliability.
* You can later upgrade it to use VS Code settings if needed.
* The API endpoints used are:
  * `POST /external/prompts/async`
  * `GET /external/prompts/{id}/response-on`

***

### 🆘 Troubleshooting

| Issue                              | Cause                           | Fix                                             |
| ---------------------------------- | ------------------------------- | ----------------------------------------------- |
| “Raia error: Failed async prompt…” | Invalid Agent Key or API URL    | Double-check RAIA\_AGENT\_KEY                   |
| Always timing out                  | Reasoning taking too long       | Increase MAX\_WAIT\_MS                          |
| Output looks like raw JSON         | Agent returning structured data | Update parsing logic in `waitForPromptResult()` |

***

### 🎉 Done!

You now have a fully working, hardcoded Raia Reasoning VS Code extension ready to help modernize your codebase.

If you want a `.vsix` one-click installer or a settings-based version, just let me know!

***
