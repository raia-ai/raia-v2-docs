# Bitbucket Integration — Practical Implementation Guide

### Introduction

This document provides a narrative guide for integrating a Bitbucket repository with the RAIA agent. The primary goal of this integration is to synchronize files from a specified repository, making their content available to the AI Agent. This process enhances the agent's knowledge base with up-to-date information from your codebase or documentation, enabling more accurate and context-aware automated workflows.

### The Integration Process Overview

The integration is structured around a standard Extract, Transform, Load (ETL) pipeline. The process commences with the **extraction** of files from a designated Bitbucket repository using the Bitbucket API. These files are then **transformed** by combining them into a single, cohesive markdown file. During this transformation phase, the Manus API is utilized to generate a derivative knowledge base, enriching the content. Finally, this processed information is **loaded** into a PostgreSQL data lake hosted on Supabase. The RAIA agent accesses this data, and the entire ETL process is automated to run on a monthly schedule, ensuring the agent's knowledge remains current.

### Roles and Responsibilities

Two key roles are central to the successful implementation of this integration. The **n8n Workflow Developer** holds the primary responsibility for setting up and deploying the n8n workflows that drive the ETL process. The **RAIA Agent Engineer** provides support by assisting with the RAIA agent's configuration, ensuring that the data is correctly ingested and utilized by the AI.For more technical details on connecting n8n with Bitbucket, you can refer to the native n8n integration documentation at [https://n8n.io/integrations/bitbucket/](https://n8n.io/integrations/bitbucket/).

#### Phase 1: Planning and Preparation

The initial phase, which typically takes 2-4 hours, is focused on planning and mapping the integration. The Workflow Developer will start by identifying the target Bitbucket repository and generating the necessary API credentials with read access. A crucial part of this stage is defining the scope of the synchronization, which involves specifying the exact directories or file types to be included. The developer then maps the file content and its structure to the target schema of the data lake. This planning phase concludes with the creation of an integration architecture diagram, a list of all required APIs and credentials, and a risk mitigation plan.

#### Phase 2: Data Extraction and Transformation

This phase, estimated to take 4-6 hours, involves the technical work of extracting and transforming the data. The Workflow Developer will configure two distinct n8n sub-workflows. The first, the `Fetch and Process Bitbucket Files` sub-workflow, is responsible for retrieving the specified files from the repository. The second, the `Combine Files into Markdown` sub-workflow, then consolidates all the extracted file content into a single markdown document. During this process, data shaping logic is applied, and the Manus API is called to generate a derivative knowledge base from the combined content. The deliverables for this phase are the completed n8n sub-workflows and a sample of the final markdown file for validation.

#### Phase 3: Loading, Automation, and Synchronization

The final phase, requiring approximately 3-5 hours, is centered on loading the data and activating the automated synchronization. The Workflow Developer configures the main `Bitbucket Files ETL Orchestrator` workflow, which manages the entire ETL pipeline from start to finish. This workflow uses an "upsert" operation to efficiently load the transformed data into the PostgreSQL database, updating existing records and inserting new ones. Once the data is loaded, the Raia API is triggered to process the new information and add it to its vector store. The process concludes with scheduling the main orchestrator workflow to run automatically each month. The final deliverables include the completed main workflow, confirmation of a successful data load, and the configured monthly execution schedule.
