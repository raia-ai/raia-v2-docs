# ServiceNow Integration — Practical Implementation Guide

**Goal:** Connect ServiceNow to the AI Agent to sync case data for automated workflows and improved agent responses.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/servicenow/](https://n8n.io/integrations/servicenow/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify your ServiceNow instance URL and create API credentials.
* [ ] Define the scope of cases to be synced (e.g., specific states, assignment groups ).
* [ ] Map ServiceNow case fields to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform ServiceNow Data**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `ServiceNow - Cases -> raia` workflow to fetch case data based on the defined scope.
* [ ] Implement data shaping logic to transform the data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted data.

**Deliverables:**

* Completed n8n workflow for data extraction and transformation.
* Sample of transformed JSON data.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `ServiceNow - Cases -> raia` workflow to orchestrate the complete ETL process.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the workflow to run monthly.

**Deliverables:**

* Completed n8n workflow for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
