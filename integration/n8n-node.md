---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/EwGkQrKpAAj0jhmC3fkJ/integrations/workflow-integration/n8n-node
---

# n8n Node

View our n8n Node / Integration here: [https://n8n.io/integrations/raia/](https://n8n.io/integrations/raia/)

**Custom n8n Node** to interact with the **Raia** platform for managing AI-powered and human-led conversations via SMS, Email, or Voice.

### 🚀 Features

This node allows you to:

* Start new conversations (SMS, Email)
* Chat or prompt an agent
* Use Raia’s platform in a single, unified node

### 🔧 Node Actions

| Action                   | Description                                              |
| ------------------------ | -------------------------------------------------------- |
| Start SMS Conversation   | Initiate a conversation via SMS                          |
| Start Email Conversation | Initiate a conversation via Email                        |
| Chat with Agent          | Create a new user and start a conversation with an agent |
| Prompt an Agent          | Send a prompt to an agent                                |

### 🧩 Node Parameters

#### Common Parameters (used in most actions)



* **First Name**
* **Last Name**
* **Context** (e.g., "Support")
* **Source** (e.g., "crm")
* **fkId**
* **fkUserId**

### Channel-Specific Parameters

**SMS**

* **Phone Number**
* **SMS Introduction** (for SMS)

**Email**

* **Email Address**
* **Email Subject**
* **Email Introduction**
* **Include Signature in Email** (boolean)

### Prompt Agent

* **Prompt**

```
{
  "conversationId": "string",
  "messageId": "string",
  "userId": "string",
  "message": "string",
  "timestamp": "ISODate"
}
```

### License

[MIT](https://github.com/n8n-io/n8n-nodes-starter/blob/master/LICENSE.md)

### Readme

#### Keywords <a href="#user-content-keywords" id="user-content-keywords"></a>

* [n8n-community-node-package](https://www.npmjs.com/search?q=keywords:n8n-community-node-package)
* [raia](https://www.npmjs.com/search?q=keywords:raia)
