# Agent -to-Agent Setup

When wanting to connect Agents (allowing one agent to call another agent) we use our Functions Skill.

We provide a general Webhook that can be used if you pass the specific Agent API Key you want to call with the function.

The first step is to setup a Function under the Agent (function skill)

<figure><img src="../.gitbook/assets/Screenshot 2026-02-05 at 11.09.06 AM.png" alt=""><figcaption></figcaption></figure>

The Function Skill will pass the query to the other Agent for a response and include back into the conversation.\
\
**To Setup:**\
\
Provide Function instructions on when the Agent should call the other agent (essentially added to the core prompt for the AI to look for this prompt to trigger the function)\
\
**Webhook**

To use our generic A2A Webhook - use this URL:

[https://raia.app.n8n.cloud/webhook/e60457a0-bc4a-47c3-bae2-3b690db3dee1](https://raia.app.n8n.cloud/webhook/e60457a0-bc4a-47c3-bae2-3b690db3dee1)

Provide Function Parameters (which for this use case we just need to pass the question the user prompted into the agent

**Function Instructions:**

```
{
  "type": "object",
  "required": [
    "query"
  ],
  "properties": {
    "query": {
      "type": "string"
    }
  }
}
```

**Header Variable**

Next, add a Header Variable using the following:\
\
Header Name = Call\_Agent\_APIKEY

Header Value = { API Key of the Agent you want to call }

<figure><img src="../.gitbook/assets/Screenshot 2026-02-05 at 11.08.29 AM.png" alt=""><figcaption></figcaption></figure>



