# Salesforce Integration — Practical Implementation Guide

**Goal:** Connect Salesforce to the AI Agent to sync support cases and knowledge base articles for automated workflows and improved agent responses.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/salesforce/](https://n8n.io/integrations/salesforce/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify Salesforce instance URL and generate API credentials.
* [ ] Define the scope of data to be synced (e.g., specific case statuses, article types ).
* [ ] Map Salesforce data fields (Cases, Case Comments, Case Feeds, Articles) to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform Salesforce Data**

* **Time:** \~4-6 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `Salesforce - Cases -> raia (2 of 2)` sub-workflow to fetch cases, comments, and feeds.
* [ ] Configure the `Salesforce - Articles -> raia (2 of 2)` sub-workflow to fetch knowledge base articles.
* [ ] Implement data shaping and enrichment logic to transform the data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted data.

**Deliverables:**

* Completed n8n sub-workflows for data extraction and transformation.
* Sample of transformed JSON data.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the main workflows (`Salesforce - Cases -> raia (1 of 2)` and `Salesforce - Articles -> raia (1 of 2)`) to orchestrate the ETL process.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the main workflows to run monthly.

**Deliverables:**

* Completed n8n main workflows for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
