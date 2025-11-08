---
description: raia Connect – Feedback Tool
---

# Human Feedback

### **Overview**

The **raia** Connect **Feedback Tool** is designed to close the loop between **real-world AI Agent performance** and **continuous training improvements**.\
It integrates directly with **raia Copilot’s Human Feedback** system, allowing you to capture, review, and resolve feedback from users who interact with your AI Agents.

This powerful workflow helps your AI Training team **identify the root cause** of issues, **apply targeted fixes**, and **rapidly improve agent accuracy and reliability**.

***

### **How It Works**

#### **1. Feedback Collection in raia Copilot**

When a user interacts with an AI Agent through **raia Copilot**, they can:

* **Rate** the AI Agent’s responses (e.g., 👍 / 👎).
* **Flag incorrect or incomplete answers**.
* **Add written comments** with details on what was wrong or missing.

This feedback is **automatically sent to raia** Connect for deeper analysis.

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-03 at 10.54.37 AM.png" alt=""><figcaption></figcaption></figure>

***

#### **2. Feedback Review in raia** Connect

Inside **raia** Connect, the Feedback Tool presents:

* **Conversation transcripts** – showing exactly what was asked and how the AI responded.
* **User rating** – good, bad, or neutral.
* **Reviewer comments** – specific insights from the human reviewer.
* **Contextual data** – which agent, knowledge packs, or functions were involved.

***

#### **3. Root Cause Analysis**

Each feedback item can be examined to determine why the AI underperformed. Common causes include:

* **Source Material Issue** – outdated, incorrect, or incomplete knowledge.
* **Bad Instructions** – flawed system prompt or poorly designed agent instructions.
* **Prompting Issue** – ambiguous or confusing user question handling.
* **Missing Information** – knowledge gaps in the vector store.
* **Hallucination** – the AI invented information not present in the training data.
* **Function Error** – connected APIs or workflows failed.

***

#### **4. Assigning & Resolving Feedback**

The AI Training team can:

* **Assign feedback** to specific team members.
* **Document the resolution** (e.g., “Added missing documentation to knowledge base” or “Updated agent prompt for clarity”).
* **Mark feedback as resolved** once fixes are in place.
* **Re-run simulations** to confirm the issue is fixed before deploying changes.

***

#### **5. Continuous Improvement Cycle**

By managing feedback systematically:

1. **Collect** → Human reviews in raia Copilot.
2. **Analyze** → Identify cause in raia Connect.
3. **Fix** → Update knowledge, prompts, or functions.
4. **Verify** → Test changes via simulations.
5. **Deploy** → Push improvements live.

This cycle ensures your AI Agents become more accurate, helpful, and aligned with user expectations over time.

***

### **Benefits**

* **Faster Training** – Structured review workflow accelerates learning.
* **Higher Accuracy** – Targeted fixes improve agent reliability.
* **Better User Experience** – Reduced frustration for end users.
* **Transparency** – Clear audit trail of issues, actions, and resolutions.
* **Scalable Governance** – Centralized tool for managing large volumes of feedback.

***

### **Best Practices**

* **Review feedback daily** to address critical issues quickly.
* **Tag feedback by category** (source data, prompt, hallucination, etc.) for trend analysis.
* **Collaborate with content owners** when issues stem from source material.
* **Use simulations** to test fixes before pushing live.
* **Close the loop** by confirming improvements with real-world interactions.

***

### **Example Workflow**

1. A customer using the **Support Agent** in raia Copilot gets an incorrect shipping policy answer.
2. They give a 👎 and write: _“The answer is outdated; our policy changed last month.”_
3. Feedback appears in raia Connect.
4. Training team investigates → finds the **shipping policy doc** in the vector store is from last year.
5. They upload the updated doc via raia Connect and re-run a simulation.
6. Simulation confirms the new answer is correct.
7. Issue is marked **Resolved**.

***
