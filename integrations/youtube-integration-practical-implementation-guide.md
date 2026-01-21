# YouTube Integration — Practical Implementation Guide

**Goal:** Connect a YouTube channel to the AI Agent to sync video transcripts for automated workflows and to provide the agent with up-to-date knowledge from your video content.**Who's Involved:**

* n8n Workflow Developer (Primary)
* RAIA Agent Engineer (Support)

See our native n8n integration at [https://n8n.io/integrations/youtube/](https://n8n.io/integrations/youtube/)

#### **Step 1: Integration Planning & Mapping**

* **Time:** \~2-4 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Generate a YouTube API key.
* [ ] Identify the specific playlist containing the videos to be synced.
* [ ] Map the video transcript content to the target schema in the data lake.
* [ ] Document system APIs, access needs, and authentication methods.

**Deliverables:**

* Integration architecture diagram.
* List of required APIs and credentials.
* Risk mitigation plan.

#### **Step 2: Extract & Transform YouTube Data**

* **Time:** \~4-6 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the `Youtube - Transcripts -> raia (2 of 2 )` sub-workflow to fetch video transcripts from the specified playlist.
* [ ] Implement data shaping logic to transform the transcript data into a structured JSON format.
* [ ] Use the Manus API for derivative knowledge base generation from the extracted transcripts.

**Deliverables:**

* Completed n8n sub-workflow for data extraction and transformation.
* A sample of the transformed JSON data.

#### **Step 3: Load Data into Data Lake and Raia**

* **Time:** \~3-5 hours
* **Owner:** Workflow Dev

**Checklist:**

* [ ] Configure the main workflow (`Youtube - Transcripts -> raia (1 of 2)`) to orchestrate the complete ETL process.
* [ ] Use the "upsert" operation to load the transformed data into the PostgreSQL database on Supabase.
* [ ] Trigger the Raia API to process the new data and add it to the vector store.
* [ ] Schedule the main workflow to run monthly to ensure the data remains current.

**Deliverables:**

* Completed n8n main workflow for data loading.
* Confirmation of data successfully loaded into the data lake and Raia.
* Monthly execution schedule configured.
