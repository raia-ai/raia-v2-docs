# Feedback Skill

## Feedback Skill

The **Feedback** skill enables administrators to process **user-submitted feedback** on AI responses.\
While end users can always leave feedback inside conversations, this skill provides a **dedicated interface** for reviewing and managing those entries.

### Overview

Administrators can:

* **View** all submitted feedback in a searchable table
* **Open** the original conversation by clicking the blue conversation link
* **Ignore** or **delete** individual feedback records
* **Export** feedback in a structured JSON format for AI training or analysis

### Feedbacks Tab

Inside the **Feedbacks** tab, administrators can:

* **Browse feedback records** in a sortable table showing
  * **Date** of submission
  * **Vote** (thumbs-up / thumbs-down)
  * **Question** and **Answer** from the conversation
  * **Comment** left by the user
  * A **Conversation** link that opens the full chat directly
* **Search** feedback by keyword or filter by time period
* **Load more results** using the page-size selector at the top left of the table.
  * Change the default (e.g., _10 per page_) to show more records at once.
* **Take action** on each record:
  * **Ignore** to mark it as reviewed without exporting
  * **Delete** to remove it entirely from the dataset

Each feedback entry is automatically compiled into a structured **JSON document** suitable for AI training and analytics.

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

### Configuration

The **Feedback Skill Config** panel allows fine-tuning of how feedback is collected and delivered.

| Setting                  | Options                                               | Description                                                                                                                   |
| ------------------------ | ----------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| **Period**               | Last 30 days · Last 60 days · Last 90 days · All time | Filters the feedback records by date range.                                                                                   |
| **Generation Mode**      | Auto · Manual                                         | **Auto** generates the feedback document automatically on schedule. **Manual** allows admins to trigger generation on demand. |
| **Auto Upload Document** | On / Off                                              | When enabled, the generated feedback document is uploaded to the AI immediately after generation for training.                |

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
