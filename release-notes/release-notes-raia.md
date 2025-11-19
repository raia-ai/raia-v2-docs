---
description: >-
  The Release Notes page provides an overview of all updates to the Raia
  platform, including new features, improvements, and bug fixes. It helps users
  and teams stay informed about the latest changes.
---

# Release Notes - raia

**November 19, 2025**\
**New Features**

*   **Default Start Page Setting Added to Copilot & LaunchPad**

    A new setting is now available in both Copilot and LaunchPad that allows users to select which page should automatically open after they log in. Users can choose between LaunchPad or Copilot, and the platform will redirect them accordingly on each login.

    The selected preference is saved across sessions and synchronized between Copilot Settings and LaunchPad Profile Settings.
*   **Add Profile Photo to User Account**

    The User Account page now supports uploading a personal profile photo. Users can add, update, or remove their profile image, improving personalization across conversations, activity logs, and team views. If no photo is uploaded, a default avatar with user initials is displayed automatically. The feature follows the same design and behavior as the Agent avatar settings, ensuring consistency across the platform.

**Improvements**

* **New Model Option: GPT-5.1 Reasoning**\
  A new model option, GPT-5.1 (Reasoning), is now available in raia2.\
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
  Added a new Escalation Skill that automatically detects escalation intent during a chat — for example, when a user says _“I want to talk to a human.”_ When triggered, the system sends notifications via email, SMS, or webhook to designated escalation recipients. \
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
  Replaced the static _Conversation Details_ block in Copilot’s sidebar with a collapsible accordion component.\
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



