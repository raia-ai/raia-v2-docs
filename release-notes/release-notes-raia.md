---
description: >-
  The Release Notes page provides an overview of all updates to the Raia
  platform, including new features, improvements, and bug fixes. It helps users
  and teams stay informed about the latest changes.
---

# Release Notes - raia

**January 16, 2026**\
**New Features**

*   **Inline Verification Setting for Live Chat**

    Introduced a new inline verification setting in Live Chat that allows enabling 2FA verification via email or SMS. Admins can configure whether verification is always required or triggered conditionally. A webhook validates the submitted code, and the user’s status is updated to “verified” upon success.
* **Password-Protected Access**\
  You can now require users to enter a password before starting a Live Chat with an AI Agent. This helps limit access to internal or sensitive agents and is configurable in Launchpad.

**Improvements**

* **Copilot Disclaimer Field Relocated**\
  The Copilot disclaimer setting has been moved from the Agent Info tab to the Copilot Skill section (under “Skills”) for better clarity and consistency. The functionality remains unchanged — the disclaimer is still editable and displays in the Copilot modal as before. Any previously saved disclaimer values were automatically migrated to the new location.
*   **Suspicious Activity Logging Enhancement**

    Suspicious conversation activity is now logged internally instead of triggering email alerts. The system captures key details like timestamp, user ID, and detection pattern, ensuring sensitive security or compliance-related events are stored centrally and not sent over email.
*   **Live Chat Height Setting**

    Added a new configuration option to adjust the Live Chat widget height, allowing users to enable full-height mode if desired.
*   **Conversation Finished Emails — User Info**

    Enhanced conversation summary emails to include user data and custom form input, improving visibility into user context.
*   **Improved Email Change Security Flow**

    Redesigned the email update process to send confirmation links to the current address first, reducing the risk of unauthorized changes and improving account recovery options.
*   **Launchpad Filters: View Deleted Conversations**

    Added a new filter in Launchpad to allow users to view conversations marked as deleted, improving transparency and supporting advanced filtering across all statuses.
*   **Organization Branding Reset**

    Introduced a new option that allows users to reset organization branding settings to default values for a clean and consistent appearance.
*   **Conversation & Feedback Enhancements**

    Added server-side conversation search, exposed timestamps, introduced message-level feedback, user listing via API, and agent token usage reporting for better analytics, compliance, and UI performance.

**Fixes**

* **Improved Space Key Behavior in Dropdown Inputs**\
  Fixed an issue in Launchpad and Copilot where pressing the space key in dropdown inputs caused unexpected behavior: the dropdown would close if the input was empty, and the space character wouldn’t be inserted if text was present. Input behavior now works as expected for both the organization and agent selectors.

***

**December 31, 2025**\
**New Features**

* **Live Chat Password Support**\
  Introduced support for password-protected Live Chat threads.
* **Support for OpenAI 5.2 Model**\
  Added full support for the OpenAI 5.2 model across the Raia platform.\
  Admins can now select this model for their AI agents to take advantage of improved performance, reasoning, and response quality.
* **File Downloads from Agent Training**\
  Added support for downloading all training documents from the agent’s training section. Users can now select and download all files in one click, streamlining access to agent training materials.
* **Editable Phone Numbers in Super Admin**\
  Enabled the ability to edit user phone numbers directly from the Super Admin panel, improving administrative control and user data management.
* **Copilot Admin Role**\
  Introduced a new user role — Copilot Admin — designed to allow users to view all conversations and perform human-in-the-loop actions without being granted access to Launch Pad or agent editing. This role ensures greater control over user permissions while enabling effective operational oversight.

**Improvements**

* **API Enhancements**\
  Expanded the API with several improvements. Now, when fetching agents via API, associated tags are also returned. A new endpoint allows token usage tracking per agent with optional date range filtering. Additionally, feedback functionality was added to messages, enabling thumbs up/down, comments, and answer tagging via API.
* **Dropdown Option for Live Chat Form**\
  Added support for “Select” dropdown fields in the Live Chat form configuration.\
  Admins can now include dropdowns as part of pre-chat forms to collect structured input from users more efficiently.
* **Fixed Sidebar Position on Dashboard**\
  The left activity sidebar (navigation panel) is now consistently fixed on the left side across all RAIA applications, including Copilot and Launchpad. It stays visible during scrolling, maintains consistent behavior across products and browsers.
* **Customizable Live Chat Button Text**\
  Added a new setting allowing customization of the text on the Live Chat button, including both the headline and sub-header. This enables teams to better tailor the chat interface to match their branding and user engagement strategies.
* **Live Chat Dark/Light Mode Support** \
  Implemented support for both Dark Mode and Light Mode in the Live Chat interface.&#x20;
* **Live Chat Disclaimer: Markdown Support**\
  Updated the disclaimer field in the Live Chat widget to support Markdown formatting, ensuring consistency with the first message styling and enabling clearer, more structured communication.

**Fixes**

* **Origins Whitelist Fix**\
  Resolved an issue with the origins whitelist configuration to ensure that only approved sources are allowed access to the platform. This fix improves security and prevents unauthorized cross-origin requests.
* **LaTeX Message Rendering in Chat UI**\
  Resolved an issue where messages containing LaTeX-style formatting (e.g. math-like expressions) were not being displayed in the chat interface, despite being correctly processed by the AI. The messages now render as expected, improving visibility and reducing confusion during testing and document preparation.

***

**December 17, 2025**\
**New Features**

* **Download AI-generated files**\
  Users can now download files generated by the AI agent directly from the chat interface. Previously, links to files were displayed but not functional. With this update, clicking the link opens and downloads the file seamlessly, improving usability when interacting with AI-generated content.
*   **Unified Left-Side Navigation Panel Across All RAIA Apps**

    Introduced a consistent left-side navigation panel across all internal RAIA app pages, including Copilot, built-in apps, and future custom apps. This ensures a seamless user experience and easy navigation between apps without leaving the RAIA environment. The sidebar is hidden for Copilot-only users to avoid confusion. Custom apps (iFrame-based) are now required to display within the same shell with the sidebar visible.

**Improvements**

*   **Improved Country Selection in Live Chat Geographic Restrictions**

    The country dropdown in Live Chat → Geographic Restrictions is now sorted alphabetically (A–Z), making it easier for users to find and select countries. Additionally, users can now jump to a country by typing the first letter on the keyboard. This change improves overall usability without affecting the logic behind geographic restrictions.

**Fixes**

*   **Fixed Missing Metadata in Live Chat Notifications**

    Resolved an issue where metadata collected from the Live Chat form was not included in the admin notification triggered via the Notification Skill. Now, all submitted data is properly passed and displayed in the notification, ensuring admins receive complete context from the conversation.

***

**December 10, 2025**\
**New Features**

* **Support for Creating Organizations via API**\
  Added the ability to programmatically create organizations through the API. This enables streamlined integration with external systems and automation of org management workflows.
* **Organization-Level Custom Branding (White Labeling)**\
  Organizations can now fully customize their branding under **Org Settings > Customize**. Admins can configure the brand name, logo, links to terms and support pages, and adjust key UI pages like Invite, Signup, and Welcome. This enables a tailored white-labeled experience for clients and users.

**Improvements**

* **Stored Streamed Reasoning in Copilot Threads**\
  Copilot now stores streamed reasoning responses from the API and displays them in the relevant message thread. This allows users to review past reasoning logic directly within the Copilot interface, improving traceability and context.
* **Async Message Status Field Added to API Endpoint**\
  The async message check endpoint now returns a `status` field with values like `running`, `completed`, or `error`, along with optional `message` and `error` keys. This provides clearer insight into message processing states for external integrations.
* **SuperAdmin Control: Edit Organization Name in SuperAdmin Panel**\
  SuperAdmins can now directly update organization names from the Organization Management screen in the Admin Panel, improving administrative flexibility and reducing reliance on backend changes.
* **Webhook Trigger on Manual Live Chat End**\
  Live Chat conversations now trigger the webhook immediately when manually marked as "done" by the user, instead of relying solely on the timeout logic. This provides better control over conversation lifecycle handling and improves integration responsiveness.
* **Chat Custom Fields API Support**\
  Introduced API support for managing custom fields in Live Chat. This enables external systems to dynamically create, update, and retrieve chat-specific metadata for enhanced integration and automation.
* **Custom Fields in Live Chat Form**\
  Admins can now add custom fields to the Live Chat pre-chat form, enabling better data collection tailored to specific business needs. Field labels, input types, and required status can be fully configured via the UI.
* **User-Level Configuration for 2FA**\
  Added support for configuring two-factor authentication (2FA) at the individual user level, allowing for more granular control over login security preferences within organizations.

**Fixes**

* **Corrected Default Prompt for Conversation Scoring Logic**\
  Updated the system prompt used in the Scoring Skill to correctly interpret gray scores as “in progress” rather than “0 = bad communication.” The explanation now aligns with backend scoring logic, improving clarity in scoring summaries.
* **Optimized Webhook Logging to Reduce Noise**\
  Reduced excessive webhook log generation by limiting the default logging window to one day. This prevents performance overhead and improves visibility by focusing on the most relevant recent activity.

***

**December 04, 2025**\
**New Features**

* **Copilot: Personalized Prompt Settings Added**\
  Added a new customizable prompt option allowing users to set personal instructions for their conversations with an agent. These instructions apply only to the user’s chats and can be configured through a new settings modal accessible from the Copilot sidebar and message composer.

**Improvements**

* **Unified Filters Panel** \
  Conversations filters were consolidated into a single panel for a cleaner, more consistent experience.
*   &#x20;**File-Only Message Support**

    Added support for sending messages that contain only an attached file without requiring any text.

    This update increases flexibility for users who need to share documents, images, or other files without typing a message.
*   **Escalation Webhook Now Sends Full Conversation Payload**

    Updated the escalation skill so that when it triggers a webhook, it now includes the full conversation payload instead of only sending the form submission. This aligns escalation behavior with other webhook types and ensures downstream systems receive complete context.
*   **Dynamic Agent-Based Navigation on Copilot Home Page**

    Enhanced the user experience on the Copilot Home Page by removing the previously empty left navigation panel. Instead of displaying an empty sidebar on initial load, the system now loads only the list of agents. When a user selects an agent, the left navigation dynamically populates with the relevant conversation history for that agent. This change improves UI clarity and reduces visual clutter on first load.
*   **Webhook Trigger Added for Unavailable Chat State**

    Implemented a webhook trigger for the “Chat currently unavailable” state, aligning it with the behavior used when conversations end. This ensures downstream systems are notified consistently via the Webhook skill.

**Fixes**

* **Live Chat & Copilot: Geographic Restrictions Behavior Fixes**\
  Improved how geographic restrictions are applied: Live Chat now shows a clear warning when a restricted user tries to send a message, the chat no longer appears active while blocked, and Copilot is no longer affected by Live Chat restrictions—conversations are created normally regardless of region. This fix ensures consistent behavior and prevents missing conversations.
*   **Reasoning Text Formatting**

    Resolved an issue where reasoning blocks displayed headings without proper line breaks. Updated formatting now ensures clear separation between reasoning steps and improves readability across all conversations.
*   **Cross-Organization Prompt Response Access Blocked**

    Resolved an issue where an agent could retrieve another organization’s prompt response using an API key not associated with the originating org. The API now enforces strict ownership validation, ensuring that only the agent who initiated a prompt can access its results.
*   **Calendar Skill API Key Validation**

    Resolved an issue where the Calendar skill could be saved even when an invalid or incorrectly formatted API key was entered. The system now properly validates API keys and blocks saving until a valid key is provided, preventing misconfigured calendar setups.
*   **Escalation Skill: Incorrect Response**&#x20;

    Resolved an issue where the Escalation skill returned unrelated prompts (e.g., document-upload requests) instead of the configured escalation response after a conversation was escalated. The skill now consistently returns the correct response defined in the escalation settings.
*   **Duplicate Uploads in Vector Store When Uploading Large Files**

    Resolved an issue where large file uploads to the Vector Store appeared to “fail” in the UI, causing the system to repeatedly retry the upload. Although the file successfully uploaded on the backend, these retries created duplicate entries in the Vector Store. The upload process now correctly reflects success/failure states and prevents duplicate vector records from being generated.
* **Email Autofill Conflict Handling Improved**\
  Fixed an issue where the system autofilled an already-taken email address based on the agent’s name without validation. Now the system checks for availability and adjusts the address if needed, with a clearer error message shown to users.
*   **Intermittent Agent Response Failures**

    Fixed an issue where agents would occasionally stop responding without error messages. The system now reliably detects and handles stalled response states to ensure consistent agent replies across sessions.

***

**November 25, 2025**\
**New Features**

*   **EU Production Deployment Launched**

    Added a fully hosted EU deployment of RAIA, running on dedicated EU servers.

    This ensures improved compliance with regional data regulations and provides EU-based customers with faster, localized performance.

**Improvements**

*   **Live Chat: Welcome Message on Chat Start**

    Added a new configurable in-chat welcome message that appears when a user opens a new conversation.

    This creates a more engaging chat entry experience and prevents users from landing on an empty chat window when no predefined questions are set.
*   **Copilot Functionality Packaged into a Dedicated Skill**

    The existing Copilot functionality, previously built directly into the agent interface—has now been formalized and packaged into a standalone&#x20;
*   **Live Chat & Copilot: Added Support for .json and .md Files**

    Expanded the list of supported file types in Live Chat and Copilot uploads.

    Users can now upload JSON (.json) and Markdown (.md) files in addition to existing text formats.

    This enhancement improves compatibility with common developer workflows and internal documentation formats.
*   **Launch Pad: Navigation Cleanup**

    Moved Conversation States, Logs, and Resource Usage into the Settings section of the Launch Pad for a cleaner, more consistent navigation structure.
*   **Delete Multiple Files at Once**

    Added the ability to remove several uploaded documents in a single action. This update streamlines document management and makes cleanup significantly faster and more convenient.
*   **Trial Experience and Payment Screen Update**

    Updated the trial logic and visibility rules for licenses.

    \
    **Fixes**
*   **Live Chat: Auto-Finish Logic Restored (EU Prod. Deployment)**

    Fixed an issue where inactive conversations were not being marked as Finished, preventing scoring and summaries from being generated. Conversations now close correctly based on inactivity, and summaries and scores are produced as expected.
*   **Conversation Status Visible to Users in Copilot**

    Updated the Copilot inbox so that end users can now see the status of their conversations (e.g., New, Escalated, Assigned) — not just admins.
*   **Live Chat: File Upload Icon Not Showing with GPT-5.1**

    Fixed an issue where the file upload icon did not appear in Live Chat when using the GPT-5.1 model.

    The supported file types configuration has been updated to correctly include GPT-5.1, ensuring the upload button displays as expected.
*   **Report Skill: Email Sending Issue Resolved**

    Fixed a bug where the Report Skill failed to send an email if only one recipient was provided.

    The report now sends correctly regardless of whether there is one or multiple email addresses.
*   **Tokens per Conversation Calculation Corrected**

    Fixed an issue where the Tokens per Conversation metric displayed incorrect values in the Resources Usage section.

    The calculation now reflects accurate token usage across all conversations.
*   **Mobile View: Unexpected Zooming Fixed**

    Resolved an issue where the screen automatically zoomed in when typing into input fields on mobile devices. Input interactions on iOS Safari and Android Chrome now work without unwanted zooming, providing a smoother mobile experience.

***

**November 19, 2025**\
**New Features**

*   **Default Start Page Setting Added to Copilot & LaunchPad**

    A new setting is now available in both Copilot and LaunchPad that allows users to select which page should automatically open after they log in. Users can choose between LaunchPad or Copilot, and the platform will redirect them accordingly on each login.

    The selected preference is saved across sessions and synchronized between Copilot Settings and LaunchPad Profile Settings.
*   **Add Profile Photo to User Account**

    The User Account page now supports uploading a personal profile photo. Users can add, update, or remove their profile image, improving personalization across conversations, activity logs, and team views. If no photo is uploaded, a default avatar with user initials is displayed automatically. The feature follows the same design and behavior as the Agent avatar settings, ensuring consistency across the platform.

**Improvements**

* **New Model Option: GPT-5.1 Reasoning**\
  A new model option, GPT-5.1 (Reasoning), is now available in raia2. In addition, this new model allows you to set the reasoning level to 'none' greatly increasing speed while working with the latest model (at the cost of the internal reasoning effort).\
  This update adds full support for selecting the 5.1 Reasoning model in the Agent Advanced Settings section, allowing agents to leverage improved reasoning capabilities where needed.
*   **Live Chat & Copilot — Character Limit Enhancement + Validation**

    Expanded the maximum allowed message length to 100,000 characters in both Live Chat and Copilot.

    Additionally, input validation has been added: if the user attempts to type more than the allowed limit, the system blocks the message and shows a clear warning.
*   **Delete Multiple Documents in raia Training**

    The Training Documents section now supports bulk deletion, allowing users to remove several files at once or delete all documents. The interface has been updated to simplify handling large document sets, making training data cleanup faster and more efficient.
*   **Chat Continuity When Context Window Limit Is Reached**

    A new mechanism now ensures chat continuity when the model reaches its maximum context window. This prevents interruptions, avoids loss of conversation flow, and maintains a smooth user experience even during long or complex chats.
*   **Login Rate Limit & Error Messaging Improvements**

    A new rate-limit rule has been added for login attempts: after more than five failed password entries, users will now receive a clear rate-limit error.

    Additionally, the login flow now distinguishes between incorrect credentials and server-side issues. If a login cannot be completed due to a server problem, users will see an appropriate message indicating a system error rather than an invalid credentials warning.
* **Activity Logs for Conversation History Download, Document Upload to Memory, and Rating Action**\
  Activity logging has been expanded to include three new user actions: downloading conversation history, uploading documents to Memory, and submitting or updating a conversation rating. Each action now generates a structured activity entry with a timestamp, user information, and relevant details, appearing consistently in the Activity section of the conversation record.&#x20;
*   **Live Chat – Background Style Options**

    The Live Chat Skill now supports selecting how the background color is rendered.

    A new setting allows choosing between Gradient and Solid background styles, giving more control over the visual appearance of the chat launcher.

    This update improves customization flexibility and allows Live Chat to better match various brand requirements.

**Fixes**

* **Auditor Skill — fixed inconsistent processing of sensitive files**\
  Resolved an issue where the Auditor Skill triggered correctly on sensitive files but did not always complete the analysis. All sensitive file types are now processed consistently as expected.

***

**November 12, 2025**\
**Improvements**

*   **Live Chat: Automatic Pop-Up Frequency Setting**

    Added a new configuration option that lets admins control how often the Live Chat widget automatically opens for visitors. The previous binary setting (“Automatic Open Chat: Yes/No”) is now expanded to three options — No, Once Per Session, and Every Time — providing more flexible behavior and improved user experience.
*   **Live Chat: Updated “Close Chat” Behavior**

    Improved the Live Chat closing flow by replacing the old “Close Chat” action with a new End Chat option. When selected, the chat session is formally ended and the user is prompted to provide a rating before the window closes. The original “Close Chat” label is now updated to Close Window for clarity.
*   **Copilot: Real-Time Skill & Function Status During Streaming Responses**

    Added live, human-readable status indicators that display what the AI is doing during a streaming response. The status chip now appears above the streaming message and updates through the full lifecycle (e.g., preparing, retrieving info, calling tools, drafting response). The indicator fades out once the final token is delivered.
*   **Usage Summary: Unified Number Formatting for Tokens Per Conversation**

    Updated the Usage Summary to apply consistent number formatting to the “Tokens Per Conversation” metric. Large values now include comma separators and proper rounding to match the formatting used across other usage statistics.
*   **Copilot Activity Tab Updates**

    The Activity Tab has been improved to provide a clearer and more structured view of the conversation history. It now displays consistent titles, timestamps, and a unified system author (“raia”). All key events—such as conversation start, status updates, scoring, feedback, and system actions—are shown in a more readable format.&#x20;
*   **Escalation Skill: New “Alerts” Tab**

    A new Alerts tab has been added to the Escalation Skill to improve visibility into triggered escalation events. The tab provides list of all escalation logs for the selected agent and aligns the UI with the existing Auditor Skill.

***

**November 5, 2025**\
**New Features**

* **Conversation Assignment**\
  Added the ability to assign conversations to other users in Copilot. Admins can now reassign threads, track assignment history, and control access, improving collaboration and workflow management.
* **Live Chat File Uploads**\
  Added file upload support to the Live Chat Skill, allowing users to attach and send documents or media during conversations.&#x20;
* **Voice-to-Text (Dictation) Support for Copilot**\
  Introduced voice dictation in Copilot, allowing users to speak messages that are automatically transcribed into text in real time. Enhances accessibility and provides a faster, hands-free chat experience.

**Improvements**

* **Custom API Key Indicator**\
  Added an indicator in the Agents view to show which agents were created using custom API keys (OpenAI or VAPI), making it easier to distinguish between system and external keys.
* **Auditor Skill: Email and SMS Notifications**\
  Extended the Auditor Skill to support additional notification channels — Email and SMS — alongside Webhook. Admins can now define multiple recipients and select preferred delivery methods for alerts.
* **“Leave Page?” Confirmation Modal**\
  Added a confirmation modal that appears if a user attempts to navigate away while an image generation process is still running. Prevents accidental interruption of ongoing jobs across Agent, Pack, and Admin screens.
* **Copilot Input Limits — Uploads and Text Paste**\
  Added configurable limits for document uploads and pasted text in Copilot. Upload size is now restricted (e.g., 10 MB), and pasted text length is capped (e.g., 30,000 words) to improve performance and stability.
* **Reasoning Support Indicator**\
  Added a visible note in Agent → Advanced Settings to indicate whether the selected AI model supports Reasoning Mode, helping users choose appropriate models for analytical or multi-step reasoning tasks.

**Fixes**

* **Web Scraping Skill**\
  Resolved an issue where web scraping tasks using Apify were not properly uploading results to Raia. The skill now reliably syncs scraped data after task completion.
* **Vector Store Upload Errors**\
  Resolved an issue where files uploaded to the Vector Store were appearing twice, displaying incorrect error messages, and not deleting properly when toggled off.

***

**October 31, 2025**\
**New Features**

* **Escalation Skill**\
  Added a new Escalation Skill that automatically detects escalation intent during a chat — for example, when a user says “I want to talk to a human.” When triggered, the system sends notifications via email, SMS, or webhook to designated escalation recipients. \
  This skill helps route urgent or sensitive cases to human agents quickly and efficiently.
* **Auditor Skill**\
  Added a new Auditor Skill for automatic conversation security and compliance checks. Detects PII, potential hack/abuse content, and supports a custom auditing rule.
* **Organization-Level Conversation States**\
  Is an organization-level tool for managing the lifecycle of conversations in Copilot. It allows org admins to create, edit, reorder, and delete custom conversation states with unique names and colors, helping teams track progress and maintain consistency across conversations.
* **Live Chat Feedback in Copilot**\
  Users can now rate their conversations directly in the Copilot interface using a star rating system. Submitted ratings are saved with each conversation and can be viewed in conversation details and reports.

**Improvements**

* **Custom Integrations for Skills via API Keys**\
  Expanded the API Keys section to support external service integrations. Organizations can now use their own API keys for select skills and services such as VAPI.
* **JSON Schema Output for Agents**\
  Added support for configuring JSON Schema as an output type in Advanced Settings. Admins can now enable “JSON Schema Output” and define schema structure directly in a text field.
* **“Optimize with AI” in Prompt Editors**\
  Added an AI-assisted rewrite option to all prompt editors, helping users refine clarity, tone, and structure automatically.
* **Mobile Settings View Redesign**\
  Updated the Copilot mobile settings layout to match the cleaner and more modern design. The new layout improves readability, spacing, and visual hierarchy for better usability on small screens.
* **Production Stability Improvement**\
  Resolved a stability issue in the raia-api service that caused crashes in production. The root cause was identified in the liveness probe configuration, and the replica count was adjusted from dynamic to static to ensure consistent availability.
* **Feedback Details on API**\
  The API now includes the email address of the user who left feedback on a conversation message. This makes it easier to see who submitted each feedback item when viewing conversation data.

**Fixes**

* **Copilot First Message Display**\
  Resolved an issue where the user’s first message in Copilot temporarily disappeared for a few seconds before the assistant’s response appeared.\
  The fix ensures that the initial message now remains visible in the chat thread immediately after submission, providing a smoother and more consistent user experience.
* **Duplicate Account Creation by Email Case**\
  Resolved an issue where users could create duplicate accounts using the same email address if one was entered in uppercase and another in lowercase.\
  The system now enforces automatic conversion of all email inputs to lowercase during registration and authentication to ensure unique account identification and prevent duplicates.

***

**October 21, 2025**\
**New Features**&#x20;

* **Reasoning Mode & File Search Enhancements**\
  Added a new “Reasoning” dropdown in Agent Advanced Settings for models supporting reasoning capabilities (e.g., GPT-5, o-series).\
  Users can now select reasoning depth: Low, Medium, or High.\
  Also introduced the ability to configure the max\_num\_results parameter in file search to fine-tune retrieval performance and result precision.

**Improvements**

* **Access Control for File Downloads**\
  Updated file permission rules to enhance data security.\
  Now, only organization owners and agent owners can download files associated with training, feedback, memory skills, and scraping.\
  This update ensures sensitive training and feedback data remain protected.
* **Copilot: Collapsible “Conversation Details” Panel**\
  Replaced the static Conversation Details block in Copilot’s sidebar with a collapsible accordion component.\
  By default, the section is now collapsed on load to reduce visual clutter and improve scannability.
* **Copilot Center Pane UI Updates**\
  Redesigned the center pane in Copilot for a cleaner and more intuitive chat experience.\
  Prompt buttons have been removed from the main Copilot interface (they remain available in Live Chat).\
  The chat input field is now positioned directly below the greeting message, improving visual flow and reducing unnecessary spacing.
* **Copilot: Message Input + Icon Rail**\
  Redesigned the chat input with a compact icon rail on the left side.\
  All actions (attach, admin mode, personalization, etc.) remain available.

**Fixes**

* **AI Model Behavior with File Search**\
  Resolved an issue where the AI produced off-topic or irrelevant answers when File Search or Vector Store was enabled but returned no results.\
  The model now correctly recognizes empty search results and avoids generating unrelated responses, improving overall accuracy and reliability.
* **Agent Response Stability & Context Window Limit**\
  Resolved an issue where the Agent could stop responding during long conversations due to exceeding the context window token limit.\
  This fix improves model stability and ensures continuous, reliable responses even in extended chats.
* **Citation Formatting in Copilot**\
  Fixed a visual formatting issue where citation tags appeared incorrectly in Copilot responses (e.g., stacked or merged citation blocks).\
  Citations now render cleanly and consistently, improving readability and maintaining the professional appearance of AI-generated responses.
* **Mobile Table Formatting in Copilot**\
  Resolved a mobile layout issue where tables and long, unbroken text strings in Copilot responses caused the interface to stretch beyond the screen width.\
  Tables are now wrapped in a responsive scrollable container, allowing smooth horizontal scrolling while keeping the overall layout constrained to the mobile viewport.
* **Weekly Report Email Delivery Check**\
  Resolved an issue where weekly report emails were not being consistently sent to customers.\
  This fix restores reliable email notifications for all active users and organizations receiving weekly reports.

***

**October 13, 2025**\
**New Features**&#x20;

* **Copilot & Live Chat Streaming**\
  Implemented real-time message streaming in Live Chat for faster, smoother interactions.\
  Messages now appear progressively as they are generated, creating a more dynamic and responsive chat experience for users.

**Improvements**

* **Live Chat: Text Wrapping Fix**\
  Updated message formatting in Live Chat and Copilot to prevent long text strings from creating horizontal scrolls.\
  Text now wraps automatically within the chat container, keeping content readable and neatly contained on all screen sizes.
* **Live Chat: Home Button Removed**\
  Removed the Home button from the Live Chat interface to simplify the layout and reduce visual clutter.\
  This change improves the overall user experience and aligns the chat design with Copilot’s updated interface.
* **Chat Composer Anchoring Enhancement**\
  Improved the message composer behavior in Copilot.\
  The composer now smoothly transitions and anchors to the bottom of the screen after the first message is sent or received, providing a more natural and consistent chat flow.

**Fixes**

* **User Role Switching in Copilot**\
  Fixed an issue preventing admins from changing a user’s role from User to Copilot User within the organization management panel.\
  This update restores proper role-switching functionality, ensuring that user permissions and access rights are updated immediately after the change.
* **Database Migration Stability Fix**\
  Resolved an issue causing migration failures during deployment and environment synchronization.\
  The update ensures stable migrations across dev, QA, and production, preventing rollout interruptions and improving backend reliability
* **API Timeout with GPT-5 Models**\
  Resolved an issue causing timeout errors when using GPT-5 models through the prompt API endpoint.\
  The fix adjusts endpoint timeout handling and improves response stability, ensuring consistent performance for agents using GPT-5 models.
* **Feedback List Refresh Fix**\
  Resolved an issue where deleted feedback items remained visible in the list until a manual page refresh.\
  The list now updates instantly after deletion, maintaining accurate counters and preserving the user’s filters and pagination context.

***

**October 3, 2025**\
**New Features**

*   **Account Deletion Option (Apple App Store Requirement)**

    Added a “Delete Account” link under Profile → Settings. When selected, the user’s account is flagged for deletion in 7 days.

    This meets Apple’s requirement for providing users with a clear way to request account deletion directly within the app.
*   **Cancel Scraping API Integration**

    Added the ability to stop an active scraping process directly from the interface.

    This allows users to cancel running data extractions without waiting for completion, improving control and responsiveness during API operations.
*   **API — Create Agent via API**

    Added support for creating new Agents directly through the API.

    This endpoint enables programmatic Agent setup with configurable parameters such as role, public/internal names, disclaimer, instructions, model, creativity, and enabled skills.

**Improvements**

*   **Copilot — Redesigned Right-Side Conversation Drawer**

    Introduced a reimagined right-hand drawer in Copilot for improved usability and organization.

    The drawer now includes enhanced structure for Info, Conversations, Activity, and Feedback tabs, plus an always-visible toggle for easier navigation.
*   **Email Skill — Disable Human-in-the-Loop in Passive Mode**

    Updated the Email Skill behavior to automatically disable the Human-in-the-Loop feature when operating in Passive Mode.

    This ensures smoother automated email processing and eliminates unnecessary human intervention in passive workflows.
*   **Live Chat — Display All Form Fields in Copilot**

    Updated the Copilot interface to ensure that all user-submitted fields from the Live Chat form (including Company) are properly displayed in the right-side info panel.

    This provides agents with complete context during conversations and ensures no form data is missed.
*   **UI Fixes — Design System Alignment**

    Aligned the visual presentation across the platform to match the design system (Copilot, Skills Section).

    Standardized typography, spacing, buttons, icons, and badges for consistent appearance and accessibility across all themes and screen sizes.
*   **Live Chat — Constrain “Experience View” to Viewport Height**

    Updated the Live Chat layout for both Agent Info and Agent Skill “Experience View” screens to match the browser viewport height, ensuring consistent scrolling behavior and usability.

**Fixes**

*   **Instructions Not Selected After Wizard Setup**

    Fixed an issue where the agent’s instructions were not automatically selected or applied after completing the setup wizard.

    Users previously had to manually reselect the instructions after setup.
*   **File Search Activation for New Agents**

    Fixed an issue where the File Search settings were not automatically enabled when creating a new Agent.

    File Search is now activated by default to ensure immediate document search functionality.
*   **Subscription Limits Bug**

    Fixed an issue where subscription usage limits were not updating correctly, causing agents to either exceed their plan limits or be restricted prematurely.

    Limits now refresh accurately in real time according to the user’s active plan.
*   **\[DEVOPS] Monitoring Alert Notifications to Slack**

    Fixed an issue where infrastructure monitoring alerts were not being delivered to Slack channels.

    Notifications now trigger reliably for all monitored services and environments.
*   **Live Chat Popup Behavior**

    Fixed an issue where the Live Chat popup would repeatedly appear for the same user on a website.

    The popup now appears only once per user session—after being closed, it will not reopen for that user.
*   **Number Formatting Issue in Assistant Replies**

    Fixed an issue where numbers were sometimes displayed with math-style formatting (e.g., $87$ instead of 87).

    The renderer now correctly displays plain numerals unless the content explicitly represents a math expression or currency.
*   **Copilot Code Block Formatting**

    Fixed an issue where code blocks rendered in Copilot were misaligned or clipped.

    The Copy button now displays correctly, and long code snippets are contained within scrollable, monospace boxes for better readability.
*   **Mobile Dropdown Minimum Width**

    Added a minimum width to the Copilot agent dropdown in mobile view to prevent name truncation when agent names are short.

    Ensures consistent layout and readability across screen sizes.

***

**September 25, 2025** \
**New Features**

*   **OpenAI Image API Support**

    Added integration with OpenAI Images. Agents can invoke image generation (and, where enabled, edits/variations) via workflows/skills. Uses the org’s OpenAI key and existing safety controls.
*   **Calendar Skill (Cal.com Integration)**

    New skill to connect an agent to Cal.com by API key. Fetches event types, lets you select one to expose, and enables availability checks and booking.
*   **Email Skill: Passive Mode**

    Added Active/Passive toggle. In Passive, inbound email updates the conversation and triggers existing webhooks/notifications, but no outbound reply is sent. Assistant drafts are saved in-thread with a “Not sent (Passive)” badge. Admin-only setting.

**Improvements**

*   **Live Chat: Removed Bottom Nav Bar**

    Dropped the 3-tab bottom bar to simplify the UI and free vertical space. Navigation to Home remains via close/back; the old “Rate” entry from the bar is temporarily unavailable.
*   **Scoring Skill: 1–10 Guidance**

    Added a non-editable inline disclaimer reminding editors to use a 1–10 scale. If a custom prompt yields a value outside 1–10, the badge shows a warning style.
*   **Copilot: Conversation Sidebar Refresh**

    Streamlined list cards, added quick filters, clearer AI/human markers, unified state/score badges, and a simpler actions menu for faster triage.
*   **Copilot & Live Chat: Cleaner AI Messages**

    AI responses now render without a filled bubble; user messages keep their bubbles. Markdown, lists, citations, and code blocks are supported (code blocks keep their own background).
*   **Copilot: AI Message Meta Row**

    Re-aligned meta under each AI message into a single left-aligned row (timestamp, feedback, status chips, web-search/citation badges). On mobile the row may wrap to two lines.
*   **LaunchPad /conversations: Expanded Search**

    Search and filters now cover Agent Name, User Name, User Email, Source, Score, Status, State and User Phone (digits-only, prefix matching).&#x20;
*   **Vector Store: Safer “Replace” Flow**

    Moved the action to its own section, changed the button to secondary, disabled it until a new store is selected, and added a confirmation modal.
*   **Super Admin: Subscription End Date on Create Organization**

    Added a required “Subscription end date” shown when a plan is selected. Prefills from plan duration (editable) and validated to be in the future and ≥ start date.

#### Fixes

*   **Score Badge Contrast (Light Theme)**

    Updated text/background so the 1–10 value is clearly readable in Light theme.

***

**September 17, 2025** \
**New Features**

* **OpenAI Image API Support** \
  Added support for the OpenAI Image API, enabling generation and retrieval of images directly through the platform.

**Improvements**

* **Scoring Skill: Disclaimer and Badge** \
  Added a disclaimer in Scoring Skill settings clarifying that scores must be within the 1–10 range, improved visibility of the score badge in Light Theme to ensure numeric values are clear and meet accessibility contrast standards, and introduced a defensive UX mechanism where scores outside the valid range display in a high-contrast warning style.

**Fixes**

* **UI & Accessibility Updates** \
  General UI improvements to ensure consistent rendering of score badges across Light and Dark themes.&#x20;

***

**September 15, 2025**\
**New Features**

* **Login with Apple**\
  Added support for authentication via Apple ID. Users can now log in securely with their Apple accounts in addition to existing options.
* **Live Chat: Configurable Icon**\
  Introduced settings in Live Chat that allow customization of the launcher icon, including size, spacing, and placement on the webpage. This enables better integration with third-party websites and improved user experience.

**Improvements**

* **Live Chat Dropdown Action**\
  Updated the action menu in the Live Chat interface.&#x20;
* **Web Scraping Limit Increased**\
  Expanded the page scraping limit from 1000 to 3000 pages, allowing users to capture and process larger websites more effectively.

**Fixes**

* **Deployment Stability**\
  Fixed an issue with raia-ui deployment where some files were missing from the storage bucket. The deployment process is now stable and complete.

***

**September 12, 2025**\
**New Feature**

* **Ability to Change Vector Store in Agent**\
  Added the ability to change the vector store assigned to an agent. This provides greater flexibility in managing knowledge bases by allowing users to switch between different vector stores without recreating the agent. It ensures smoother data management, easier updates, and more efficient use of resources.

***



