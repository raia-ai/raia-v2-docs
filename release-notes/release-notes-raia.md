---
description: >-
  The Release Notes page provides an overview of all updates to the Raia
  platform, including new features, improvements, and bug fixes. It helps users
  and teams stay informed about the latest changes.
---

# Release Notes - raia

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
* **\[DEVOPS] Database Migration Stability Fix**\
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



