# System Logs and Debug

## Log Information

This **Log Information** panel is part of a debugging or monitoring tool for tracking AI or API activity logs. When you click on a specific log entry in the debug interface, it displays detailed metadata about that event, including:

* **ID**: A unique identifier for the log entry or request.
* **Created Date**: The exact timestamp when the action occurred (e.g. _12:09 PM, 20 Jul 2025_).
* **Source**: The origin of the request (e.g., which application or environment triggered it).
* **Action Name**: The specific function, operation, or event that was executed.
* **Status**: Indicates whether the operation succeeded, failed, or encountered an error (e.g., _SUCCESS_).
* **Summary**: A brief description or result of the action taken.
* **Organization ID**: Identifies the organization/account associated with the request.
* **User ID**: Tracks which user initiated the action.
* **Agent ID**: Identifies which AI agent or service handled the request.

In short, this view helps developers or admins monitor and troubleshoot actions, calls, or events made within their AI system.

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

## Organization Information

The **Organization Information** section in the debug menu provides key administrative details about the organization linked to the AI platform or service. It tracks the following elements:

* **ID**: A unique identifier for the organization within the system.
* **Name**: The official name of the organization (e.g., _RAIA LAUNCHPAD_).
* **Created Date**: The timestamp when the organization profile or workspace was first created (e.g., _11:53 AM, 15 Mar 2025_).
* **Updated Date**: The last time any change or update was made to the organization’s information or settings (e.g., _1:52 PM, 12 May 2025_).
* **Status**: Indicates the current state of the organization account (e.g., _ACTIVE_, which means it’s operational and in use).

In summary, this section helps track when the organization was onboarded, its current activity status, and its unique identifiers for internal system referencing.

<figure><img src="../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

## Agent Information

The **Agent Information** section in the debug menu provides detailed metadata about the AI agent handling interactions. It keeps track of the following elements:

* **ID**: A unique system-generated identifier for the AI agent.
* **Name**: The internal name or role assigned to the agent (e.g., _CARLY - AUTO SALES QUALIFIER_).
* **Public Name**: The name shown to users or customers during interactions (e.g., _CARLY_).
* **Status**: Indicates the operational state of the agent (e.g., _ACTIVE_, meaning it's currently enabled and available for use).
* **Organization ID**: Links the agent to its parent organization by ID.
* **Created Date**: The exact date and time the agent was created in the system (e.g., _3:34 PM, 11 Jun 2025_).
* **Updated Date**: The last time the agent’s data, settings, or configuration was modified (e.g., _12:25 PM, 8 Jul 2025_).

This section is useful for identifying the agent’s purpose, managing its lifecycle, and tracking its changes over time within the broader organizational context.

<figure><img src="../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

## Details

The **Details** section in the debug menu displays the full JSON structure of the data payload that was sent or received during an AI interaction, even when it's empty or partially filled. It serves as a template or raw data log showing the fields the system expects or uses.

In this case, it includes:

* **fKId**: The unique identifier for the interaction record.
* **email / source / channel / context**: Fields intended to capture communication metadata (who it's for, where it's from, what it’s about).
* **fKUserId**: Links this interaction to a specific user in the system.
* **lastName / firstName**: User’s contact details.
* **customData > missionContactId**: Used to track the mission or campaign this contact belongs to.
* **emailSubject / smsIntroduction / emailIntroduction**: The message content prepared for delivery.
* **includeSignatureInEmail**: Boolean flag indicating whether to append a signature to the email.

Even though most fields are blank in this example, it helps developers validate the request structure and debug issues like missing data or formatting errors.

<figure><img src="../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

