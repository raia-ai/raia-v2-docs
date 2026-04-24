# Salesforce Integration — Practical Implementation Guide

### Introduction

This guide provides a detailed narrative for integrating Salesforce with the RAIA agent. The core purpose of this integration is to establish a dynamic connection that syncs support cases and knowledge base articles from Salesforce directly into the AI Agent's knowledge base. This synchronization facilitates automated workflows and equips the agent with comprehensive, up-to-date information, resulting in more effective and contextually accurate user interactions.

### The Integration Process Overview

The integration is built upon a standard Extract, Transform, Load (ETL) framework. The process begins with the **extraction** of key data—including Cases, Case Comments, Case Feeds, and Articles—from your Salesforce instance via its API. This raw data is then **transformed** into a structured JSON format. A crucial part of this stage is the use of the Manus API to generate a derivative knowledge base, which enriches the original content. In the final step, the transformed data is **loaded** into a Supabase-hosted PostgreSQL data lake. The RAIA agent then accesses this repository for its operational knowledge. The entire cycle is automated to execute monthly, ensuring the agent's information is consistently refreshed.

### Roles and Responsibilities

Two primary roles are essential for a smooth integration. The **n8n Workflow Developer** leads the charge, focusing on the configuration and deployment of the n8n workflows that power the ETL pipeline. The **RAIA Agent Engineer** provides crucial support, assisting with the agent's configuration and ensuring that the synced data is correctly indexed and utilized by the AI.For additional technical specifications on the n8n-Salesforce connection, please consult the native n8n integration documentation at [https://n8n.io/integrations/salesforce/](https://n8n.io/integrations/salesforce/).

#### Phase 1: Planning and Preparation

The initial phase, requiring approximately 2-4 hours, is dedicated to meticulous planning. The Workflow Developer starts by identifying the Salesforce instance URL and generating the necessary API credentials for secure communication. Following this, a clear scope for data synchronization is defined, specifying which case statuses or article types will be included. The developer then undertakes the critical task of mapping the Salesforce data fields to the target schema of the data lake. This foundational phase concludes with the delivery of a comprehensive integration architecture diagram, a documented list of all required APIs and credentials, and a proactive risk mitigation plan.

#### Phase 2: Data Extraction and Transformation

This phase, estimated to take 4-6 hours, involves the hands-on development of the extraction and transformation workflows. The Workflow Developer configures two specific n8n sub-workflows: `Salesforce - Cases -> raia` to handle the retrieval of cases, comments, and feeds, and `Salesforce - Articles -> raia` for fetching knowledge base articles. Within these workflows, sophisticated data shaping and enrichment logic is implemented to convert the Salesforce data into the required JSON structure. The Manus API is also integrated at this stage to generate the derivative knowledge base. The successful completion of this phase is validated by the finalized n8n sub-workflows and a sample of the transformed JSON data.

#### Phase 3: Loading, Automation, and Synchronization

The final phase, with an estimated duration of 3-5 hours, focuses on loading the data and activating the automated synchronization schedule. The Workflow Developer configures the main orchestrating workflows, `Salesforce - Cases -> raia` and `Salesforce - Articles -> raia`. These workflows employ an "upsert" function to efficiently load the data into the PostgreSQL database, which intelligently updates existing records and adds new ones. Once the data is successfully loaded, the Raia API is triggered to process and index the new information. The process culminates in scheduling the main workflows for automatic monthly execution. The final deliverables include the fully configured main workflows, a confirmation of the successful data load, and the established monthly run schedule.
