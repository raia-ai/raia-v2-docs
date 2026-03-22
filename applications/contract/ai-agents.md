# AI Agents

In RAIA Contract, **AI Agents** are the intelligent engines that perform the automated review and redlining of your documents. An agent is a configurable connection to an AI service, equipped with specific instructions and credentials to analyze contracts according to your standards. Understanding how to configure and utilize agents is key to tailoring the platform to your specific legal and business requirements.

### The Role of AI Agents

Agents are the operational core of the platform, responsible for the most critical step in the workflow: the automated review. Their primary functions are:

* **Document Analysis**: When you initiate a review, the selected agent receives the document content and analyzes it based on its underlying AI model and configuration.
* **Redlining**: The agent generates a "redlined" version of the document, which includes suggested additions, deletions, and modifications. This is returned to the platform as tracked changes.
* **Specialization**: By creating multiple agents, you can specialize them for different tasks. For example, you could have one agent trained to review Non-Disclosure Agreements (NDAs) and another specialized in Master Service Agreements (MSAs).

### Agent Configuration

When you create an agent in RAIA Contract, you define several key properties that govern its behavior.

| Property          | Description                                                                                                                                              |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Name**          | A unique, descriptive name to help you identify the agent (e.g., "NDA Review Agent").                                                                    |
| **API Key**       | The secure credential that allows the agent to authenticate with the AI service. This key is encrypted for security.                                     |
| **Webhook URL**   | The endpoint that the AI service will call to send the redlined document back to RAIA Contract. This enables the asynchronous processing workflow.       |
| **Agent Type**    | A field to classify the agent, which can be used for organizational purposes.                                                                            |
| **Default Agent** | You can designate one agent as the **default**. This agent will be automatically selected for all new document uploads, streamlining the review process. |

### The Asynchronous Workflow

The interaction with AI agents is designed to be **asynchronous**. This is a crucial concept to understand.

1. When you start a review, RAIA Contract sends the document to the agent.
2. The platform does **not** wait for an immediate response. Instead, it marks the document as "Processing."
3. The AI agent performs its analysis, which may take some time depending on the document's length and complexity.
4. Once finished, the agent sends the redlined content back to the **Webhook URL** it was configured with.
5. RAIA Contract receives this callback, updates the document with the redlined version, and changes its status to "Completed." You are then notified that the review is ready.

This asynchronous model ensures that the user interface remains responsive and that you can continue working on other tasks while the AI review is in progress.

### Managing Your Agents

The **Settings > Agents** section of the platform is your control center for managing all your AI agents. Here, you can:

* **Create**, **edit**, and **delete** agents.
* **Set a default agent** to be used for all new documents.
* **View the configuration** of each agent, including its webhook URL and type.

By creating and configuring specialized AI agents, you can transform RAIA Contract from a general-purpose review tool into a highly customized platform that enforces your organization's specific legal and business standards.
