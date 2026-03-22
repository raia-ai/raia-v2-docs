# Versions

**Versions** are a critical feature in RAIA Contract that provide a complete and auditable history of your document's lifecycle. A version is a snapshot of your document at a specific point in time, capturing the state of its content, segments, and redlines. This version control system is fundamental to a compliant and transparent contract management process.

### The Purpose of Version Control

Effective version control serves several key purposes:

* **Audit Trail**: It creates an undeniable record of who changed what and when. This is crucial for compliance and for resolving any disputes that may arise during negotiation.
* **Historical Reference**: You can easily look back at previous versions of the document to understand how it has evolved. This can provide valuable context during a complex negotiation.
* **Mistake Recovery**: If you make a mistake or want to revert a set of changes, you can easily restore a previous version of the document.
* **Comparison**: The platform allows you to compare different versions, providing a clear overview of the changes made between any two points in the document's history.

### How Versioning Works

RAIA Contract automatically creates new versions of your document at key moments in its lifecycle:

* **Initial Upload**: The original, uploaded document is saved as Version 1.
* **AI Review Completion**: When the AI agent returns its redlined suggestions, a new version is created.
* **Manual Saves**: As you review the document and accept or reject changes, you can manually save your progress, creating a new version.

Each version is stored in the `document_versions` table and includes:

* The full content of the document at that point in time (as a collection of segments).
* A version number.
* A timestamp.
* The user who created the version.
* Optional notes that you can add to describe the changes made in that version.

### The Version History Interface

The **Version History** feature, typically found in a sidebar or tab within the document review interface, provides a complete list of all versions of your document. From this interface, you can:

* **View all versions** in chronological order.
* **See who created each version** and when.
* **Read the notes** associated with each version.
* **Compare any two versions** to see the differences between them.
* **Restore a previous version**, which will make that version the new current state of the document.

By providing a robust and easy-to-use version control system, RAIA Contract ensures that you never lose track of your document's history. This feature provides the safety net and auditability required for a professional and compliant contract review process. The final article in this section will cover **Tags**, the primary tool for organizing your documents.
