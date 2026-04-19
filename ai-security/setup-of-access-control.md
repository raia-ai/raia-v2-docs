---
metaLinks:
  alternates:
    - >-
      https://app.gitbook.com/s/EwGkQrKpAAj0jhmC3fkJ/launch-plan/ai-security/setup-of-access-control
---

# Setup of Access Control

## 🔐 Setting Up Access Control in Raia v2

### Overview

Access control in **raia v2** ensures that users interact with AI Agents and organizational data based on clearly defined roles and permissions. This system operates across **three levels**:

1. **Moderator Level** (Raia staff)
2. **Organization Level** (Your company and team)
3. **Agent Level** (Individual AI Agents)

Each level has distinct user roles and capabilities. Here's how to configure and manage access at each level.

***

### 🏢 Organization-Level Access

These roles define what users can do within your company’s account.

#### **Org Owner**

* Full access to the organization
* Can manage users, agents, packs, functions, subscriptions
* Can create, edit, and delete agents
* Can assign access to others

#### **Org Admin**

* Nearly identical permissions to Org Owner
* Can manage agents and users within the organization
* Cannot delete the organization

#### **Org User**

* Can interact with agents
* Cannot edit or configure agents
* Cannot manage users or settings

Copilot User

* Only Access Agents when shared by other Admin
* Only access Agent via Copilot App

***

### 🤖 Agent-Level Access

These roles control what a user can do with a specific AI Agent.

#### **Agent Owner**

* Full access to the Agent
* Can change settings, train the agent, assign skills, upload documents
* Can grant/revoke agent access to other users
* Can delete the agent

#### **Agent Admin**

* Almost full access like Owner, but **cannot delete or transfer ownership** of the agent

#### **Editor**

* Can configure skills and content
* Can use the agent
* **Cannot delete or reassign** the agent or access its training data

#### **Authenticated User**

* Requires login (magic link, code, or authentication)
* Can interact with the agent in its intended use case (chat, SMS, etc.)

#### **Public User**

* Anonymous access
* Limited to front-end agent interfaces (e.g. public live chat)

***

### 🎛️ How to Assign Access

You can assign or revoke roles from the **Agent Settings > Security tab** or the **Organization Management > Users section**:

1. **Add a New User**:
   * Go to `Users` > `Add User`
   * Enter email, assign organization and/or agent roles
2. **Change User Role**:
   * Navigate to the user’s profile
   * Edit their Org or Agent level roles as needed
3. **Remove Access**:
   * Under user details, choose "Revoke Access" from the Org or Agent they are assigned to
4. **Set Always Admin Mode** _(Copilot)_:
   * For agent admins, this enables visibility into all agent threads
   * Found in personal settings in Copilot app

***

### 🧠 Quick Reference: Role Capabilities Matrix

| Role               | Manage Org | Manage Users | Create Agent | Train Agent | View Threads | Upload Docs     | Delete Agent |
| ------------------ | ---------- | ------------ | ------------ | ----------- | ------------ | --------------- | ------------ |
| Super Admin (Raia) | ✅          | ✅            | ✅            | ✅           | ✅            | ✅               | ✅            |
| Org Owner          | ✅          | ✅            | ✅            | ✅           | ✅            | ✅               | ✅            |
| Org Admin          | ✅          | ✅            | ✅            | ✅           | ✅            | ✅               | ✅            |
| Org User           | ❌          | ❌            | ❌            | ❌           | ✅            | ❌               | ❌            |
| Agent Owner        | ❌          | ❌            | ✅ (Agent)    | ✅           | ✅            | ✅               | ✅            |
| Agent Admin        | ❌          | ❌            | ❌            | ✅           | ✅            | ✅               | ❌            |
| Editor             | ❌          | ❌            | ❌            | Partial     | ✅            | ❌ (if disabled) | ❌            |
| Authenticated User | ❌          | ❌            | ❌            | ❌           | ✅            | ❌               | ❌            |
| Public User        | ❌          | ❌            | ❌            | ❌           | ✅            | ❌               | ❌            |

***

### 🌍 Organization-Level Data Access Modes (For Packs & Functions)

* **Private**: Only the creator can access
* **Public**: Available within the organization
* **Global**: (Raia-only) Available across all organizations

***

### 🔐 Advanced Controls

* **Live Chat Skill Restrictions**: Limit by IP or Country (Geographic Restrictions)
* **Training Feedback**: Only Admins can add threads to agent memory
* **Document Upload Restrictions**: Disable for non-admin users in agent settings
* **Webhook & API Access**: Must be set up by Agent Admins or Owners

***

### Summary

Use these access levels to confidently manage who can build, test, launch, or interact with your AI Agents in raia v2. Whether you’re scaling to thousands of users or just starting out, access control is your first line of governance.&#x20;

{% embed url="https://youtu.be/xmSAs-WfyF8" %}
