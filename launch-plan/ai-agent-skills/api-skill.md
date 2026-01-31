# API Skill

Here’s a full breakdown of how to **configure and set up the API Skill** in **raiaAI’s Launch Pad**. This skill allows you to **interact with your AI agent programmatically** via RESTful API endpoints—perfect for integrating the agent into custom software, workflows, or apps.

***

<figure><img src="../../.gitbook/assets/Screenshot 2025-04-17 at 10.21.18 AM.png" alt=""><figcaption></figcaption></figure>

The API Documentation can be [found here](https://api.raia2.com/api/external/docs).

Each Agent has an API Key which you generated under the API Skill when editing the Agent,

Pass the API Key via the header as **Agent-Secret-Key**

**Example**&#x20;

```
curl -X POST https://your-api-endpoint.com/endpoint \
  -H "Content-Type: application/json" \
  -H "Agent-Secret-Key: XXXXXXXXXX" \
  -d '{
    "firstName": "Greg",
    "lastName": "Giglio",
    "channel": "sms",
    "context": "You are talking with mortgage lead Greg Giglio. Their email is XXXXXXXX Their phone is XXXXXXX. They previously spoke with Andrew S. Russell at RCG Mortgage. You are reconnecting with this opportunity to see if they are in the market for a mortgage.",
    "source": "CRM",
    "fkId": "12345",
    "fkUserId": "123456789", 
    "email": "demo@demo.com",
    "phoneNumber": "+14567890101", 
    "smsIntroduction": "Hi, Greg. It's Mindy"
  }'

```

#### 🔗 **API Skill Overview**

The **API Skill** gives developers access to:

* **Agent-level endpoints** (create/update/manage agents)
* **Conversation-level endpoints** (start, fetch, and update threads)
* **Prompt & response data** (enable fine-tuned logic or storage)

You can:

* Send user messages to your agent and get responses
* Retrieve transcripts or logs
* Create custom interfaces or workflows around the agent

***

#### 🛠 **API Skill Setup Guide**

***

**1. Enable the API Skill**

* Go to **Agent → Skills**
* Click **Add Skill**
* Select **API Skill** and toggle it **Active**

***

**2. Generate API Credentials**

Once the skill is enabled:

* Navigate to **Settings** (or the "API & Integrations" tab if present)
* Click **“Generate Secret Key”**
  * This is your **Bearer Token** for authorization
  * Store this securely — it's required for all requests

You may also receive:

* Agent ID
* Organization ID (for multi-agent setups)

***

**3. Available Endpoints (Typical Examples)**

Here’s what you can do:

| Endpoint                              | Function                                 |
| ------------------------------------- | ---------------------------------------- |
| `POST /api/conversations/start`       | Start a new thread                       |
| `POST /api/conversations/:id/message` | Send message to an existing conversation |
| `GET /api/conversations/:id`          | Get conversation data                    |
| `GET /api/agents/:id`                 | Fetch agent info                         |
| `PUT /api/agents/:id`                 | Update agent configuration               |
| `GET /api/prompts/:id`                | Retrieve prompt data                     |
| `GET /api/threads`                    | List all conversations (admin only)      |

***

**4. Authentication**

All requests must include an **Authorization header**:

```
Agent-Secret-Key: XXXXXXXXXX
```

You can also assign keys **per organization** or **per agent** depending on access controls.

***

**5. Webhook Integration (Optional)**

For two-way communication, combine with the **Webhook Skill** to:

* Receive messages or summaries asynchronously
* Trigger real-time updates to external apps after agent replies

***

**6. Test API Usage**

Use tools like:

* **Postman** or **cURL** for quick testing
* **Swagger UI** (if available) for interactive exploration

Verify:

* Agent responds as expected
* Secure access is enforced
* Rate limits or usage quotas (if applicable)

***

#### ✅ **Best Practices**

| Tip                             | Why It Helps                                     |
| ------------------------------- | ------------------------------------------------ |
| Rotate keys regularly           | Enhances security                                |
| Use unique keys per integration | Isolates systems and simplifies auditing         |
| Limit API scope                 | Follow least-privilege principle for endpoints   |
| Combine with Scoring & Webhooks | Enables powerful analytics & follow-up workflows |

## [API Setup Video](https://www.youtube.com/watch?v=xwRKF_VovT8)

{% embed url="https://www.youtube.com/watch?v=xwRKF_VovT8" %}
