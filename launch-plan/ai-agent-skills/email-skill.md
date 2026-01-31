# Email Skill

Here’s a full breakdown of how to **configure and set up the Email Skill** in **raiaAI’s Launch Pad**. This skill allows your AI agent to send and receive emails using a customizable sender identity and message structure.

***

<figure><img src="../../.gitbook/assets/Screenshot 2025-04-17 at 10.10.40 AM.png" alt=""><figcaption></figcaption></figure>

#### 📧 **Email Skill Setup Guide**

**1. Configure Sender Details**

These details control the "From" information in the emails your agent sends.

*   **Name of Sender (Required):**\
    Set the display name of the sender, e.g.:

    > _“Ava from Acme Support”_
*   **Email Address (Required):**

    * A system-assigned email ending in `@raiabot.com` will be auto-filled.
    * **You may edit** this to use a custom domain (see below).

    ✅ _Example:_ [_support@yourcompany.com_](mailto:support@yourcompany.com) _(if verified)_

***

**2. Set Up Message Content**

Define how your agent introduces itself and closes emails.

*   **Default Subject Line (Required):**\
    Controls the subject of all outbound emails unless overwritten by the campaign or function.

    > _“Quick follow-up from your recent inquiry”_
*   **Default Email Introduction (Required):**\
    This is the opening paragraph of every message. Keep it warm, clear, and professional.

    > _“Hi! I’m your AI assistant here to help. If you need a human, just reply and I’ll loop someone in.”_
*   **Email Signature (Required):**\
    A branded, friendly sign-off.

    > _“Cheers,_\
    > &#xNAN;_&#x41;va – Your Acme Support Assistant”_

🧠 **Pro Tip:** Use the **“Optimize with AI”** button to refine your intro or signature content with GPT-based suggestions.

***

**3. Custom Domain Setup (Optional but Recommended)**

To send emails from your domain (e.g., [hello@yourcompany.com](mailto:hello@yourcompany.com)), you need to configure domain settings.

* **Add Domain Button:**\
  Opens a modal to add a custom domain.
* **Setup Button (for each domain):**\
  Launches instructions and DNS records for domain verification (DKIM/SPF, etc.)
* **Status Indicator:**
  * ✅ Verified (Ready to send from your domain)
  * 🕒 Pending (DNS setup in progress)&#x20;

***

**4. Send a Test Email**

* Use the **Send Test** button to send a sample email to yourself or a teammate.
* Verifies formatting, branding, and deliverability.

***

**5. Save Settings**

* Once everything is configured, click **Save** to activate the Email Skill for your agent.

***

#### 🧾 Summary Checklist

| Section             | Required | Editable After Setup | Notes                               |
| ------------------- | -------- | -------------------- | ----------------------------------- |
| Name of Sender      | ✅        | ✅                    | Your brand’s display name           |
| Email Address       | ✅        | ✅                    | Can use custom domain               |
| Subject Line        | ✅        | ✅                    | Sets default subject                |
| Email Introduction  | ✅        | ✅                    | Auto-included in all emails         |
| Signature           | ✅        | ✅                    | Adds a closing to each message      |
| Domain Verification | ❌        | ✅                    | Optional, but boosts deliverability |
| Send Test Email     | 🚫       | ✅                    | For preview only                    |
| Save Settings       | ✅        | N/A                  | Finalize setup                      |

***

## [Email Setup Video](https://www.youtube.com/watch?v=KLK-19EnBmo)

{% embed url="https://www.youtube.com/watch?v=KLK-19EnBmo" %}
