# Freshdesk Integration — Practical Implementation Guide

**Goal:** Connect Freshdesk to the AI Agent to sync support tickets and solution articles for automated workflows and improved agent responses.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/freshdesk/](https://n8n.io/integrations/freshdesk/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify Freshdesk instance URL and generate API credentials.
* [ ] Define the scope of data to be synced (e.g., specific ticket statuses, solution categories ).
* [ ] Map Freshdesk data fields (Tickets, Conversations, Solutions) to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform Freshdesk Data**

* **Time:** \~4-6 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `Freshdesk - Tickets -> raia (2 of 2)` sub-workflow to fetch tickets and their conversations.
* [ ] Configure the `Freshdesk Solutions` workflow to fetch solution articles.
* [ ] Implement data shaping and enrichment logic to transform the data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted data.

**Deliverables:**

* Completed n8n sub-workflow for ticket extraction and the full workflow for solutions.
* Sample of transformed JSON data for both tickets and solutions.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the main workflow (`Freshdesk - Tickets -> raia (1 of 2)`) to orchestrate the ETL process for tickets.
* [ ] Verify the `Freshdesk Solutions` workflow is correctly configured to load data into the data lake.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the main workflows to run monthly.

**Deliverables:**

* Completed n8n main workflows for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
