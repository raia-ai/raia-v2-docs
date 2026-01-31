# Calendar Skill

The **Calendar** skill integrates with [Cal.com](https://cal.com) to help AI agents manage appointments and scheduling tasks.

\
It provides a seamless booking experience that syncs with multiple calendar providers.

### Overview

With this skill, an agent can:

* **Create** calendar events
* **View** existing appointments
* **Update** scheduled events
* **Delete** events when necessary

<figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Authentication

To enable the skill, supply a valid **Cal.com API token**.\
This token authenticates the agent and grants permission to perform calendar actions on the user’s behalf.

<pre><code>Required: Cal.com API Token
<strong>Purpose : Authorize create / view / update / delete operations
</strong></code></pre>

### Prompt Integration

The agent’s **system prompt** should include instructions that:

1. Inform the AI when scheduling is appropriate.
2. Describe how to call the Calendar skill when a user mentions booking, rescheduling, or checking availability.

These prompt rules allow the agent to recognize scheduling-related requests and respond with the correct calendar management actions.
