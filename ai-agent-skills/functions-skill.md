# Functions Skill

Here’s a complete breakdown of how to **configure and set up the Functions Skill** in **raiaAI’s Launch Pad**. This skill allows your AI agents to **execute backend functions**—such as retrieving CRM data, booking appointments, triggering actions in other software, or querying databases—based on user intent.

***

<figure><img src="../.gitbook/assets/Screenshot 2025-04-17 at 10.35.28 AM.png" alt=""><figcaption></figcaption></figure>

#### 🧩 **Functions Skill Overview**

The **Functions Skill** empowers your agent to:

* Run **custom logic** like `get_lead_status`, `schedule_meeting`, `fetch_order_status`
* Use **real-time data** from external sources
* Interact with APIs, internal databases, or third-party services

This brings dynamic capabilities to your agent beyond static knowledge or basic Q\&A.

***

#### 🛠️ **Functions Skill Setup Guide**

***

**1. Enable the Skill**

* Navigate to your agent's **Skills tab**
* Click **“Add Skill”**
* Choose **Functions** from the list and toggle it **Active**

***

**2. Add a New Function**

Go to the **Functions Library** (can be global or agent-specific):

* Click **“Create Function”**
* Define the following:

**🧾 Function Definition Fields**

| Field             | Description                                                           |
| ----------------- | --------------------------------------------------------------------- |
| **Name**          | Identifier for the function (e.g., `get_user_profile`)                |
| **Description**   | What the function does—shown to the AI agent to decide when to use it |
| **Inputs**        | Define expected parameters (e.g., `email`, `user_id`, `date`)         |
| **Outputs**       | Describe expected response data                                       |
| **Endpoint URL**  | The webhook/API endpoint the function hits                            |
| **Method**        | Choose `GET`, `POST`, `PUT`, etc.                                     |
| **Headers**       | Include any required headers (e.g., Authorization keys)               |
| **Body Template** | If POST, define dynamic JSON payload using input variables            |
| **Test Button**   | Use mock values to verify the function runs correctly                 |

You can also add logic for:

* **Success/Failure Handling**
* **Fallback responses**
* **User-friendly error messages**

***

**3. Function Usage in Agent Conversations**

Once the function is created:

* The AI agent can **automatically decide** when to call it based on user prompts
* Example:\
  User: _"Can you check the status of my order?"_\
  → Agent: _(detects intent)_ → calls `get_order_status` function → returns result to user

***

**4. Testing & Validation**

* Use **Copilot** to simulate conversations
* Verify the function is:
  * Triggered under the right conditions
  * Receiving valid input/output
  * Returning readable and useful results to users

***

**5. Organize & Reuse**

* Save commonly used functions in the **Global Functions Library**
* Functions can be reused across multiple agents

***

#### ✅ **Best Practices**

| Tip                                  | Why It Helps                                                      |
| ------------------------------------ | ----------------------------------------------------------------- |
| Use clear descriptions               | Helps the LLM know when to trigger the function                   |
| Include default values in test cases | Speeds up validation                                              |
| Keep response outputs structured     | Easier for agent to parse and summarize                           |
| Sanitize inputs & outputs            | Ensure safe and user-friendly interactions                        |
| Monitor usage                        | Track which functions are called and how often (for improvements) |

## [Function Setup Video](https://www.youtube.com/watch?v=BbADZyiu1tw)

{% embed url="https://www.youtube.com/watch?v=BbADZyiu1tw" %}
