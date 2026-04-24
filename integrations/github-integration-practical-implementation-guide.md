# GitHub Integration — Practical Implementation Guide

### Introduction

This guide provides a narrative walkthrough for integrating a GitHub repository with the RAIA agent. The primary purpose of this integration is to synchronize files from a specified repository directly into the AI Agent's knowledge base. This ensures the agent is always equipped with the most current information from your codebase or documentation, enabling it to provide accurate responses and support automated workflows.

### The Integration Process Overview

The integration is designed around a standard Extract, Transform, Load (ETL) process. It begins with the **extraction** of files from a designated GitHub repository using the GitHub API. These files are then **transformed** by combining them into a single, cohesive markdown file. During this transformation phase, the Manus API is utilized to generate a derivative knowledge base, enriching the content. Finally, this processed information is **loaded** into a PostgreSQL data lake hosted on Supabase. The RAIA agent accesses this data, and the entire ETL process is automated to run on a monthly schedule, ensuring the agent's knowledge remains current.

### Roles and Responsibilities

Two key roles are vital for a smooth integration. The **n8n Workflow Developer** is responsible for configuring and deploying the n8n workflows that handle the ETL process. The **RAIA Agent Engineer** provides support by assisting with the agent's configuration and ensuring the synchronized data is correctly ingested and utilized by the AI.For more technical details on the n8n-GitHub connection, you can refer to the native n8n integration documentation at [https://n8n.io/integrations/github/](https://n8n.io/integrations/github/).

#### Phase 1: Planning and Preparation

The initial phase, typically requiring 2-4 hours, is dedicated to planning the integration. The Workflow Developer will start by identifying the target GitHub repository and generating a personal access token with the necessary `repo` scope. A crucial step in this phase is to define the scope of the synchronization, determining which directories or file types to sync. The developer then maps the file content and structure to the target schema of the data lake. This planning stage concludes with the creation of an integration architecture diagram, a list of required APIs and credentials, and a risk mitigation plan.

#### Phase 2: Data Extraction and Transformation

This phase, estimated to take 4-6 hours, focuses on the technical implementation of the data extraction and transformation. The Workflow Developer will configure two distinct n8n sub-workflows. The first, the `Fetch and Process GitHub Files` sub-workflow, is responsible for retrieving the specified files from the repository. The second, the `Combine Files into Markdown` sub-workflow, then consolidates all the extracted file content into a single markdown document. During this process, data shaping logic is applied, and the Manus API is called to generate a derivative knowledge base from the combined content. The deliverables for this phase are the completed n8n sub-workflows and a sample of the final markdown file for validation.

#### Phase 3: Loading, Automation, and Synchronization

The final phase, requiring approximately 3-5 hours, is centered on loading the data and activating the automated synchronization. The Workflow Developer configures the main `GitHub Files ETL Orchestrator` workflow, which manages the entire ETL pipeline from start to finish. This workflow uses an "upsert" operation to efficiently load the transformed data into the PostgreSQL database. Once the data is loaded, the Raia API is triggered to process the new information and add it to its vector store. The process concludes with scheduling the main orchestrator workflow to run automatically each month. The final deliverables include the completed main workflow, confirmation of a successful data load, and the configured monthly execution schedule.
