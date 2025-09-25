---
description: >-
  The Release Notes page provides an overview of all updates to the Raia
  platform, including new features, improvements, and bug fixes. It helps users
  and teams stay informed about the latest changes.
---

# Release Notes - raia

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



