# TeamSupport Integration — Practical Implementation Guide

**Goal:** Connect TeamSupport to the AI Agent to sync support tickets and wiki articles for automated workflows and improved agent responses.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/teamsupport/](https://n8n.io/integrations/teamsupport/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify TeamSupport instance URL and generate API credentials.
* [ ] Define the scope of data to be synced (e.g., specific ticket types, wiki categories ).
* [ ] Map TeamSupport data fields (Tickets, Actions, Wikis) to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform TeamSupport Data**

* **Time:** \~4-6 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `TeamSupport - Tickets -> raia (2 of 2)` sub-workflow to fetch tickets and their actions.
* [ ] Configure the `TeamSupport Wikis` workflow to fetch wiki articles.
* [ ] Implement data shaping and enrichment logic to transform the data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted data.

**Deliverables:**

* Completed n8n sub-workflow for ticket extraction and the full workflow for wikis.
* Sample of transformed JSON data for both tickets and wikis.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the main workflow (`TeamSupport - Tickets -> raia (1 of 2)`) to orchestrate the ETL process for tickets.
* [ ] Verify the `TeamSupport Wikis` workflow is correctly configured to load data into the data lake.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the main workflows to run monthly.

**Deliverables:**

* Completed n8n main workflows for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
