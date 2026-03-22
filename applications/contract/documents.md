# Documents

In RAIA Contract, the **document** is the central entity around which all workflows revolve. A document is not merely a static file; it is a rich, dynamic object that encapsulates the contract's content, its history, and all associated metadata. A thorough understanding of the document entity is crucial for leveraging the full power of the platform.

### The Document Data Model

A document in RAIA Contract is composed of several key pieces of information that are stored and managed in the `user_documents` table.

| Field                | Description                                                                                                                                                                                                                    |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Title**            | The name of the document, which you can edit for organizational purposes.                                                                                                                                                      |
| **Original Content** | The full text content of the document as it was originally uploaded.                                                                                                                                                           |
| **Redlined Content** | The AI-generated version of the document, containing all the suggested revisions and tracked changes.                                                                                                                          |
| **Segments**         | The document's content is broken down into a structured format (JSON) of **segments**. This allows the AI to process the document granularly and enables the side-by-side review interface.                                    |
| **Status**           | The current state of the document in its lifecycle (e.g., `pending`, `processing`, `completed`, `error`).                                                                                                                      |
| **Visibility**       | An access control setting that determines whether the document is `private` (visible only to you) or `shared` (visible to members of the current team workspace). Shared documents are associated with a team via a `team_id`. |

### Visibility and Workspaces

Document visibility behaves differently depending on **where you are in the product**: your **Personal Workspace** vs a **Team Workspace**.

#### 1) Your Personal Workspace (your own account)

* Documents default to **private** visibility.
* You can see **all documents you’ve uploaded**, regardless of whether they are private or shared.
* You can toggle a document to **shared** to make it visible to your team members.
* Only members of your team can see **shared** documents.

#### 2) When you’re in a Team Workspace (someone else’s team)

* Documents you upload are automatically set to **shared** visibility.
* The document is tagged/associated with that team via the team’s `team_id`.
* The document **belongs to you** (you are the uploader) but lives in that team’s workspace.
* All team members (and the team owner) can see it.

> Note: Private documents are only available in your Personal Workspace.

### The Document Lifecycle

A document progresses through a distinct lifecycle within the RAIA Contract platform:

1. **Upload**: The lifecycle begins when you upload a contract file. The system ingests the file, parses its content, and creates a new document record.
2. **Processing**: You select an AI agent and initiate the review. The document's status changes to `processing` as it is sent to the agent for analysis.
3. **Review**: The AI agent returns the redlined content, and the document's status changes to `completed`. The document is now ready for your review in the side-by-side comparison interface.
4. **Versioning**: As you review and make changes, you can save new **versions** of the document, creating a complete history of its evolution.
5. **Export**: Once the review is finalized, you can export the document in your desired format (e.g., .docx or .pdf).
6. **Archiving**: After the contract is executed or no longer active, you can **archive** the document. This removes it from your main dashboard but preserves its history for future reference.

### Managing Your Documents

The **Documents** section of the dashboard is your central repository for managing all your contracts. From this view, you can:

* **View all your documents** in a searchable and filterable list.
* **Track the status** of each document at a glance.
* **Organize documents** by applying custom **tags**.
* **Perform bulk actions**, such as archiving multiple documents at once.
* **Access the review interface** for any document with a single click.

By treating each document as a comprehensive record of the contract negotiation process, RAIA Contract provides a powerful system for not only accelerating your reviews but also for maintaining a complete and auditable history of your legal agreements.
