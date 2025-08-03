---
description: Using Simulation in raia Academy to Test AI Agents
---

# Simulation

### **How Simulation works**

{% embed url="https://youtu.be/fYgDJ4380pA" %}

### **Overview**

Simulation in **raia Academy** allows you to create realistic test conversations for your AI Agents before deploying them in a live environment.\
This feature lets you design **scenarios** that mimic real-world situations, run them against your agents, and then review the results in **raia Copilot** for human feedback and performance tuning.

***

### **Why Simulation is Important**

Testing your AI Agents in realistic scenarios before launch helps:

* **Identify weaknesses** in understanding or response accuracy.
* **Validate conversation flow** and ensure it aligns with your intended use case.
* **Reduce live environment errors** by catching issues early.
* **Improve training data** through targeted feedback.
* **Measure real-world readiness** without impacting real customers.

***

<figure><img src="../../.gitbook/assets/Screenshot 2025-08-03 at 10.53.49 AM.png" alt=""><figcaption></figcaption></figure>

### **How It Works**

1. **Create a Simulation**
   * Go to the **Simulation** section in raia Academy.
   * Click **Add Simulation**.
   * Choose between:
     * **Single Scenario** – Test one specific situation.
     * **Bulk Scenarios** – Upload or create multiple situations for broader testing.
2. **Define the Scenario**
   * Write a description of the test situation as if you were describing it to a human tester.
   * Example for a support agent:
     * _"A customer is contacting support to change their payment method due to a failed credit card."_
     * _"Customer reports their recent order arrived damaged and they want to return the item."_
3. **Select the Agent**
   * Pick the AI Agent you want to test from your available list.
4. **Choose Internal Type** _(if applicable)_
   * Select the type of internal test (e.g., support inquiry, sales request, technical troubleshooting).
5. **Run the Simulation**
   * Click **Create Simulation**.
   * The simulation will generate **AI-to-AI conversations** based on your scenario.
   * These conversations are sent to **raia Copilot** for review.

***

### **Reviewing & Providing Feedback in raia Copilot**

Once a simulation is complete:

1. **Open raia Copilot** and navigate to the simulation conversations.
2. Review the AI Agent’s responses:
   * Was the answer factually correct?
   * Was the tone appropriate?
   * Did the conversation resolve the scenario successfully?
3. **Rate the responses** (e.g., thumbs up/down, 1–5 stars).
4. **Provide human feedback**:
   * Suggest corrections or improvements.
   * Flag missing information or incorrect logic.
5. Feedback is automatically saved to improve the agent’s future performance.

***

### **Why Human Feedback from Simulations Matters**

* **Accuracy** – Ensures the agent’s answers are correct and useful.
* **Consistency** – Standardizes responses across similar scenarios.
* **Adaptability** – Helps the AI learn how to handle new or unexpected queries.
* **Reduced Hallucinations** – Directs the AI away from making up information.
* **Continuous Improvement** – Every simulation review makes the agent smarter.

***

### **Best Practices**

* **Simulate common customer interactions** to cover high-frequency scenarios.
* **Include edge cases** (rare or tricky situations) to test resilience.
* **Run simulations after major knowledge updates** to verify accuracy.
* **Involve multiple reviewers** to gather diverse feedback perspectives.
* **Re-run failed scenarios** after training to confirm fixes worked.

***

### **Example Workflow**

1. You update your **Support Agent**’s knowledge base.
2. You create three test scenarios:
   * Payment method change due to failed credit card.
   * Product return request for a damaged item.
   * Customer requesting shipping status update.
3. Run the simulations → AI generates test conversations.
4. Support team reviews the conversations in **raia Copilot**.
5. They rate, correct, and add feedback.
6. The agent is retrained on the updated feedback data.
7. You re-run the simulations to confirm improvement.

***
