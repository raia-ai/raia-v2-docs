# GitHub Integration — Practical Implementation Guide

**Goal:** Connect a GitHub repository to the AI Agent to sync files for automated workflows and to provide the agent with up-to-date knowledge.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/github/](https://n8n.io/integrations/github/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Identify the target GitHub repository and generate a personal access token with `repo` scope.
* [ ] Define the scope of files to be synced (e.g., specific directories, file types ).
* [ ] Map the file content and structure to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform GitHub Data**

* **Time:** \~4-6 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `Github - Files -> raia (part 2 of 3)` sub-workflow to fetch the specified files from the repository.
* [ ] Configure the `Github - Files -> raia (part 3 of 3)` sub-workflow to combine the extracted files into a single markdown file.
* [ ] Implement data shaping logic to transform the file content into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the combined file.

**Deliverables:**

* Completed n8n sub-workflows for data extraction and transformation.
* A sample of the combined markdown file and the transformed JSON data.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the main workflow (`Github - Files -> raia (part 1 of 3)`) to orchestrate the complete ETL process.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the main workflow to run monthly to ensure the data remains current.

**Deliverables:**

* Completed n8n main workflow for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
