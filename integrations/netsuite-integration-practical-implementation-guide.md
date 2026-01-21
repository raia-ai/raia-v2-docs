# Netsuite Integration — Practical Implementation Guide

**Goal:** Connect Netsuite to the AI Agent to sync support cases and solution articles for automated workflows and improved agent responses.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/netsuite/](https://n8n.io/integrations/netsuite/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify Netsuite account ID and generate API credentials (Token-based authentication ).
* [ ] Define the scope of data to be synced (e.g., specific case types, solution categories).
* [ ] Map Netsuite data fields (Support Cases, Solutions) to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform Netsuite Data**

* **Time:** \~4-6 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `Netsuite - SupportCases -> raia` workflow to fetch support cases.
* [ ] Configure the `Netsuite - Solutions -> raia` workflow to fetch solution articles.
* [ ] Implement data shaping logic to transform the data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted data.

**Deliverables:**

* Completed n8n workflows for data extraction and transformation.
* Sample of transformed JSON data for both support cases and solutions.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the workflows to orchestrate the complete ETL process.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the workflows to run monthly.

**Deliverables:**

* Completed n8n workflows for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured
