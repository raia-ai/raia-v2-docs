# Jira Integration — Practical Implementation Guide

**Goal:** Connect Jira to the AI Agent to sync issues for automated workflows and to provide the agent with up-to-date project information.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/jira/](https://n8n.io/integrations/jira/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify your Jira instance URL and generate an API token.
* [ ] Define the scope of issues to be synced by creating a JQL (Jira Query Language ) query.
* [ ] Map Jira issue fields (including comments) to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform Jira Data**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `JIRA - Issues -> raia` workflow to fetch issues using the defined JQL query.
* [ ] Implement data shaping and enrichment logic to transform the issue data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted issue data.

**Deliverables:**

* Completed n8n workflow for data extraction and transformation.
* A sample of the transformed JSON data.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `JIRA - Issues -> raia` workflow to orchestrate the complete ETL process.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the workflow to run monthly to ensure the data remains current.

**Deliverables:**

* Completed n8n workflow for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
