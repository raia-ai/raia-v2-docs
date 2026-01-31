# Documents for Training

## 📄 How to Prepare Documents for Upload into the Vector Store (Best Practices)

When training your AI Agent in **raia v2**, one of the most powerful tools you can use is the **Vector Store**—a system powered by OpenAI’s native embedding technology that enables your Agent to **retrieve relevant information from your files in real-time**.

But not all documents are created equal. The **quality and structure** of your content will directly impact how well the AI understands, retrieves, and uses the information.

This guide will walk you through **how to format your documents** for best results, file types that work well, and tips to avoid common formatting issues.

***

### ✅ What Is the Vector Store?

The Vector Store allows you to upload content that your AI Agent can use to answer questions. It converts your files into “chunks” (embeddings) and makes them **searchable by meaning**, not just keywords.

Your Agent can then pull the most relevant content from those documents during a conversation.

***

### 🧾 Recommended File Types

| File Type          | Recommended?      | Notes                                                            |
| ------------------ | ----------------- | ---------------------------------------------------------------- |
| **.md (Markdown)** | ✅✅✅               | Best for structured text with headers, bullets, and sections.    |
| **.json**          | ✅✅✅               | Ideal for structured data, Q\&A sets, or hierarchical content.   |
| **.pdf**           | ✅                 | Works well if **clean and properly formatted**.                  |
| **.docx**          | ❌ (convert first) | Better as **.json or .txt (markdown)** for context preservation. |
| **.csv**           | ❌ (convert first) | Better as **.json** for context preservation.                    |
| **.ppt/.pptx**     | ❌ (convert first) | Use only if content is exported to markdown or plain text.       |

***

### 🧼 Best Practices for Document Formatting

#### 🧠 Use Structured Formatting

* Use **headings** (`#`, `##`, `###`) to separate topics
* Use **bullet points or numbered lists** to make dense content more digestible
* Keep **sections short and focused** (\~200-500 words per section)
* For questions and answers, use a consistent format like:

```markdown
### Q: What is our refund policy?
A: Our refund policy allows returns within 30 days of purchase...
```

***

#### 📦 Convert CSV to JSON (for structured data)

CSV files flatten data and lose context. If you're uploading something like:

* Product lists
* Feature tables
* Policy matrices

👉 **Convert it into JSON** format before uploading:

**Example (CSV):**

```
Plan, Price, Support
Basic, $99, Email
Pro, $199, Chat
```

**Recommended (JSON):**

```json
[
  {
    "plan": "Basic",
    "price": "$99",
    "support": "Email"
  },
  {
    "plan": "Pro",
    "price": "$199",
    "support": "Chat"
  }
]
```

This keeps the structure and relationships intact for the AI to understand and reference.

***

#### 📝 Convert Slide Decks or Mal-Formatted PDFs

Slide decks and some exported PDFs often contain:

* Disjointed content
* Missing context
* Out-of-order text from columns or footers

🔁 **Instead of uploading the original**, copy the core content into:

* **Markdown files** for slide-by-slide explanations
* **JSON format** if you're organizing it as Q\&A, sections, or modules

**Example (Slide deck section):**

```markdown
## Customer Segments

- SMBs with 5M-20M in revenue
- Need automation but lack tech resources
- Value "done-for-you" AI agents
```

***

#### 🗂️ Split Large Files When Possible

* For very large documents (e.g. handbooks, guides), break into logical sections:
  * `employee_handbook_intro.md`
  * `employee_handbook_policies.md`
  * `employee_handbook_benefits.md`

This makes indexing faster, and chunking more precise.

***

### 🔒 Other Considerations

* **Avoid uploading private info** unless it's intended for internal agents
* **Clean up copy-pasted content** from emails, websites, or chat logs—remove footers, junk formatting, or links without context
* Use **consistent language and structure** across files for the AI to learn patterns

***

### 🧩 Recap: Format Recommendations by Use Case

| Use Case               | Recommended Format      |
| ---------------------- | ----------------------- |
| Product Lists / Tables | JSON                    |
| Policies & Procedures  | Markdown or PDF (clean) |
| Knowledge Base Content | Markdown                |
| Slide Decks            | Markdown                |
| FAQ or Support Scripts | JSON or Markdown        |
| Email/Text Transcripts | Markdown                |

***

### 🧪 Final Tip: Test What You Train

Once you upload documents:

1. Use **Copilot** to ask your Agent questions about the content
2. Confirm it's retrieving the right information
3. Tweak and re-upload if needed—think of it as a living training file

{% embed url="https://youtu.be/ywzbQw8NrW8" %}
