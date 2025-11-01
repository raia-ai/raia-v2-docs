# Agent Function Skill

<figure><img src="../../.gitbook/assets/image (42) (1).png" alt=""><figcaption></figcaption></figure>

## Multiple Functions per Agent

You have the ability to have multiple functions setup per agent

<figure><img src="../../.gitbook/assets/image (36) (1).png" alt=""><figcaption></figcaption></figure>

## Able to fully customize your AI Agent Function

Being able to fully customize your AI Agent function is important because it lets you define specific tasks the AI can perform, such as pulling data, calculating values, or interacting with tools based on user input. This enables more intelligent, action-oriented conversations where the AI doesn't just respond but actually does something useful and task-specific.

<figure><img src="../../.gitbook/assets/image (37) (1).png" alt=""><figcaption></figcaption></figure>

## Choosing a Function from a template

In an Organization it is possible to have Functions previously created, allowing you to simple import them directly into AI Agent and even further customizing them for a more specific Agent purpose.

<figure><img src="../../.gitbook/assets/image (38) (1).png" alt=""><figcaption></figcaption></figure>

## Function Name & Internal Name

The **Function Name** is the user-facing label that describes what the function does, while the **Internal Name** is used behind the scenes for system reference and integration purposes.

<figure><img src="../../.gitbook/assets/50a9ccde-c06a-4d22-bc27-7bc3b721fc94 (1).png" alt=""><figcaption></figcaption></figure>

## Function Instructions

Function Instructions are crucial because they clearly define what the AI function is supposed to do, ensuring the AI executes the task accurately and stays aligned with your intended purpose. Well-written instructions guide the model’s behavior, reduce errors, and improve reliability when triggering specific actions.

<figure><img src="../../.gitbook/assets/image (39) (1).png" alt=""><figcaption></figcaption></figure>

## Function Webhook

The "Webhook to Call" is essential in a function because it defines the external endpoint where the AI sends data to execute the task, such as fetching real-time info or triggering an external action. Without it, the function can't connect to or interact with outside systems, making the task incomplete or non-functional.

<figure><img src="../../.gitbook/assets/image (40) (1).png" alt=""><figcaption></figcaption></figure>

## Function Parameters

Function parameters are crucial because they define the inputs your AI needs to perform a task accurately, such as user details, query values, or settings. Structuring these parameters ensures the function runs dynamically and correctly based on real-time user input or context.

<figure><img src="../../.gitbook/assets/image (41) (1).png" alt=""><figcaption></figcaption></figure>

## [Function Setup Video](https://www.youtube.com/watch?v=BbADZyiu1tw)

{% embed url="https://www.youtube.com/watch?v=BbADZyiu1tw" %}

### Sample Function that calls a Webhook in n8n

Here is a function that transforms the prompt into a SQL Statement that is passed ot a n8n workflow.\


Here is the Function Parameters:

```
{
  "type": "object",
  "required": [
    "nl_statement",
    "response"
  ],
  "properties": {
    "response": {
      "type": "string",
      "description": "The SQL Query."
    },
    "nl_statement": {
      "type": "string",
      "description": "The natural language input to be converted into an SQL query."
    }
  },
  "additionalProperties": false
}
```

Here is the Function Instructions:

{% hint style="info" %}
We put the schema of our database to help the AI build the SQL Query
{% endhint %}

```
When a user asks for information about clients, customers, contacts, meetings, or deals, you will generate a SQL query to get that data. To understand how the database is organized, please consult the training documents titled "CRM Schema Dictionary.md" located in the vector store. Keep in mind that the database operates on PostgreSQL. Make sure to rely solely on the information from these documents, and do not make guesses or assumptions regarding field names or the structure of the schema.

If the user asks for information about a company or deal - you can use the ILIKE in the SQL to make sure you find the company name. 

*ALWAYS USE ILIKE* when doing keyword based searches to support lower and upper case

For example if the user asks "Give me the information on the company Click" - you can search for companies where the company name ILIKE '%click%' to make sure you return a result.

Here is the schema dictionary you will be using to generate the postgreSQL queries:

# Schema Data Dictionary

## Overview

This data dictionary documents the database schema for a Customer Relationship Management (CRM) system. The schema contains 18 tables that manage activities, companies, contacts, deals, meetings, notes, projects, and user management functionality.

## Schema Summary

| Table Name | Purpose | Primary Key | Record Count Estimate |
|------------|---------|-------------|----------------------|
| activities | Track customer interactions and tasks | id (uuid) | High |
| companies | Store company/organization information | id (uuid) | Medium |
| company_attachments | File attachments for companies | id (uuid) | Medium |
| contact_attachments | File attachments for contacts | id (uuid) | Medium |
| contacts | Individual contact information | id (uuid) | High |
| deal_attachments | File attachments for deals | id (uuid) | Medium |
| deal_audit_log | Audit trail for deal changes | id (uuid) | High |
| deal_contacts | Many-to-many relationship between deals and contacts | id (uuid) | High |
| deals | Sales opportunities and deals | id (uuid) | Medium |
| meetings | Meeting records and summaries | id (uuid) | Medium |
| notes | General notes and comments | id (uuid) | High |
| projects | Project management integration | id (uuid) | Low |
| role_audit_log | Audit trail for role changes | id (uuid) | Low |
| trello_cards | Trello integration card data | id (bigint) | Medium |
| trello_lists | Trello integration list data | id (bigint) | Low |
| user_integrations | Third-party integrations per user | id (uuid) | Low |
| user_profiles | Extended user profile information | id (uuid) | Low |
| user_roles | User role assignments | id (uuid) | Low |
| user_starred_projects | User's starred projects | id (uuid) | Low |




## Table Definitions

### activities

**Purpose**: Tracks customer interactions, tasks, meetings, and other activities within the CRM system.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the activity |
| title | text | NOT NULL | - | - | Title or name of the activity |
| description | text | NULL | - | - | Detailed description of the activity |
| type | text | NULL | - | - | Type/category of activity (e.g., call, email, meeting) |
| company_id | uuid | NULL | - | FOREIGN KEY → companies(id) | Associated company |
| contact_id | uuid | NULL | - | FOREIGN KEY → contacts(id) | Associated contact |
| deal_id | uuid | NULL | - | FOREIGN KEY → deals(id) | Associated deal |
| user_id | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who created the activity |
| activity_date | timestamp with time zone | NULL | now() | - | When the activity occurred |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |
| subject | text | NOT NULL | - | - | Subject line or brief summary |
| priority | text | NULL | - | - | Priority level (e.g., high, medium, low) |
| completed | boolean | NULL | false | - | Whether the activity is completed |
| due_date | timestamp with time zone | NULL | - | - | When the activity is due |
| location | text | NULL | - | - | Physical or virtual location |
| meeting_method | text | NULL | - | - | Method of meeting (e.g., in-person, video call) |
| assigned_to | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User assigned to complete the activity |
| organization_id | uuid | NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |

**Relationships**:
- Many-to-one with companies (company_id → companies.id)
- Many-to-one with contacts (contact_id → contacts.id)
- Many-to-one with deals (deal_id → deals.id)
- Many-to-one with auth.users (user_id → auth.users.id)
- Many-to-one with auth.users (assigned_to → auth.users.id)

### companies

**Purpose**: Stores information about companies and organizations in the CRM system.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the company |
| name | text | NOT NULL | - | - | Official name of the company |
| industry | text | NULL | - | - | Industry sector or category (what type of company it is) |
| website | text | NULL | - | - | Company website URL |
| description | text | NULL | - | - | Company description or notes |
| address | text | NULL | - | - | Street address |
| city | text | NULL | - | - | City location |
| state | text | NULL | - | - | State or province |
| country | text | NULL | - | - | Country location |
| zip | text | NULL | - | - | Postal/ZIP code |
| size | text | NULL | - | - | Company size (e.g., small, medium, large) |
| owner | text | NULL | - | - | Company owner or primary contact |
| annual_revenue | numeric | NULL | - | - | Annual revenue amount |
| tags | ARRAY | NULL | - | - | Array of tags for categorization (what type of company it is) |
| logo | text | NULL | - | - | URL or path to company logo |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |
| favorited | boolean | NULL | false | - | Whether the company is marked as favorite |
| organization_id | uuid | NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |
| google_folder | text | NULL | - | - | Associated Google Drive folder |
| google_space | text | NULL | - | - | Associated Google Workspace |

**Relationships**:
- One-to-many with contacts (id ← contacts.company_id)
- One-to-many with activities (id ← activities.company_id)
- One-to-many with deals (id ← deals.company_id)
- One-to-many with company_attachments (id ← company_attachments.company_id)
- One-to-many with meetings (id ← meetings.company_id)
- One-to-many with notes (id ← notes.company_id)


### company_attachments

**Purpose**: Stores file attachments associated with companies.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the attachment |
| company_id | uuid | NOT NULL | - | - | Associated company identifier |
| file_name | text | NOT NULL | - | - | Original name of the uploaded file |
| file_path | text | NOT NULL | - | - | Storage path or URL of the file |
| file_size | bigint | NOT NULL | - | - | File size in bytes |
| file_type | text | NOT NULL | - | - | MIME type or file extension |
| uploaded_by | uuid | NULL | - | - | User who uploaded the file |
| created_at | timestamp with time zone | NULL | now() | - | Upload timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |

**Relationships**:
- Many-to-one with companies (company_id → companies.id) [implied]

### contact_attachments

**Purpose**: Stores file attachments associated with contacts.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the attachment |
| contact_id | uuid | NOT NULL | - | FOREIGN KEY → contacts(id) | Associated contact identifier |
| file_name | text | NOT NULL | - | - | Original name of the uploaded file |
| file_path | text | NOT NULL | - | - | Storage path or URL of the file |
| file_size | bigint | NOT NULL | - | - | File size in bytes |
| file_type | text | NOT NULL | - | - | MIME type or file extension |
| uploaded_by | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who uploaded the file |
| created_at | timestamp with time zone | NULL | now() | - | Upload timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |

**Relationships**:
- Many-to-one with contacts (contact_id → contacts.id)
- Many-to-one with auth.users (uploaded_by → auth.users.id)

### contacts

**Purpose**: Stores individual contact information and lead management data.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the contact |
| first_name | text | NULL | - | - | Contact's first name |
| last_name | text | NULL | - | - | Contact's last name |
| email | text | NULL | - | - | Primary email address |
| phone | text | NULL | - | - | Primary phone number |
| company_id | uuid | NULL | - | FOREIGN KEY → companies(id) | Associated company |
| position | text | NULL | - | - | Job title or position |
| status | text | NULL | 'lead' | - | Contact status (e.g., lead, prospect, customer) |
| notes | text | NULL | - | - | General notes about the contact |
| tags | ARRAY | NULL | - | - | Array of tags for categorization |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |
| last_contacted_at | timestamp with time zone | NULL | - | - | Last interaction timestamp |
| owner_id | uuid | NULL | - | FOREIGN KEY → user_profiles(id) | User responsible for this contact |
| favorited | boolean | NULL | false | - | Whether the contact is marked as favorite |
| organization_id | uuid | NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |
| utm_source | text | NULL | - | - | Marketing attribution source |
| utm_campaign | text | NULL | - | - | Marketing campaign identifier |
| utm_content | text | NULL | - | - | Marketing content identifier |

**Relationships**:
- Many-to-one with companies (company_id → companies.id)
- Many-to-one with user_profiles (owner_id → user_profiles.id)
- One-to-many with activities (id ← activities.contact_id)
- One-to-many with contact_attachments (id ← contact_attachments.contact_id)
- One-to-many with notes (id ← notes.contact_id)
- One-to-many with meetings (id ← meetings.contact_id)
- Many-to-many with deals via deal_contacts (id ← deal_contacts.contact_id)


### deal_attachments

**Purpose**: Stores file attachments associated with deals.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the attachment |
| deal_id | uuid | NOT NULL | - | FOREIGN KEY → deals(id) | Associated deal identifier |
| file_name | text | NOT NULL | - | - | Original name of the uploaded file |
| file_path | text | NOT NULL | - | - | Storage path or URL of the file |
| file_size | bigint | NOT NULL | - | - | File size in bytes |
| file_type | text | NOT NULL | - | - | MIME type or file extension |
| uploaded_by | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who uploaded the file |
| created_at | timestamp with time zone | NULL | now() | - | Upload timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |

**Relationships**:
- Many-to-one with deals (deal_id → deals.id)
- Many-to-one with auth.users (uploaded_by → auth.users.id)

### deal_audit_log

**Purpose**: Maintains an audit trail of all changes made to deals for compliance and tracking.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the audit entry |
| deal_id | uuid | NOT NULL | - | - | Deal that was modified |
| user_id | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who made the change |
| action | text | NOT NULL | - | - | Type of action performed (e.g., create, update, delete) |
| old_values | jsonb | NULL | - | - | Previous values before the change |
| new_values | jsonb | NULL | - | - | New values after the change |
| changed_fields | ARRAY | NULL | - | - | Array of field names that were modified |
| created_at | timestamp with time zone | NOT NULL | now() | - | When the change occurred |

**Relationships**:
- Many-to-one with deals (deal_id → deals.id) [implied]
- Many-to-one with auth.users (user_id → auth.users.id)

### deal_contacts

**Purpose**: Junction table establishing many-to-many relationships between deals and contacts.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the relationship |
| deal_id | uuid | NOT NULL | - | FOREIGN KEY → deals(id) | Associated deal |
| contact_id | uuid | NOT NULL | - | FOREIGN KEY → contacts(id) | Associated contact |
| created_at | timestamp with time zone | NOT NULL | now() | - | When the relationship was established |
| updated_at | timestamp with time zone | NOT NULL | now() | - | Record last update timestamp |

**Relationships**:
- Many-to-one with deals (deal_id → deals.id)
- Many-to-one with contacts (contact_id → contacts.id)

### deals

**Purpose**: Manages sales opportunities, deals, and revenue tracking within the CRM.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the deal |
| title | text | NOT NULL | - | - | Deal title or name |
| company_id | uuid | NULL | - | FOREIGN KEY → companies(id) | Associated company |
| deal_value | numeric | NULL | 0 | - | value of setup/service fees for a deal |
| mrr | numeric | NULL | 0 | - | Monthly recurring revenue |
| status | text | NULL | 'prospect' | status = ANY (ARRAY['proposal'::text, 'qualified'::text, 'prospect'::text, 'negotiation'::text, 'closed-won'::text, 'closed-lost'::text, 'cancelled'::text]) | Current deal status |
| description | text | NULL | - | - | Detailed description of the deal |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |
| name | text | NULL | - | - | Alternative name field |
| assigned_to | uuid | NULL | - | FOREIGN KEY → user_profiles(id) | User responsible for the deal |
| organization_id | uuid | NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |
| stage_activated_at | timestamp with time zone | NULL | - | - | When current stage was activated |
| cancelled_at | timestamp with time zone | NULL | - | - | When the deal was cancelled |
| closed_date | date | NULL | - | - | Date when deal was closed |
| tags | ARRAY | NULL | - | - | Array of tags for categorization |

**Relationships**:
- Many-to-one with companies (company_id → companies.id)
- Many-to-one with user_profiles (assigned_to → user_profiles.id)
- One-to-many with activities (id ← activities.deal_id)
- One-to-many with deal_attachments (id ← deal_attachments.deal_id)
- One-to-many with notes (id ← notes.deal_id)
- Many-to-many with contacts via deal_contacts (id ← deal_contacts.deal_id)


### meetings

**Purpose**: Records meeting information, summaries, and AI-generated insights.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the meeting |
| title | text | NOT NULL | - | - | Meeting title or subject |
| summary | text | NULL | - | - | Meeting summary |
| meeting_type | text | NULL | 'internal' | - | Type of meeting (internal, external, etc.) |
| ai_summary | text | NULL | - | - | AI-generated meeting summary |
| meeting_date | text | NULL | - | - | Date of the meeting (stored as text) |
| video_link | text | NULL | - | - | Link to meeting recording or video |
| organization_id | uuid | NOT NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |
| created_at | timestamp with time zone | NOT NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NOT NULL | now() | - | Record last update timestamp |
| created_by | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who created the meeting record |
| contact_id | uuid | NULL | - | FOREIGN KEY → contacts(id) | Associated contact |
| company_id | uuid | NULL | - | FOREIGN KEY → companies(id) | Associated company |
| highlights | text | NULL | - | - | Key highlights from the meeting |
| next_steps | text | NULL | - | - | Action items and next steps |
| attendees | ARRAY | NULL | - | - | Array of meeting attendees |
| meeting_id | text | NULL | - | - | External meeting system identifier |
| company_name | text | NULL | - | - | Company name (denormalized) |
| meetingScore | smallint | NULL | - | - | Meeting quality or success score |
| longDescription | text | NULL | - | - | Extended meeting description |
| follow_up_meeting | text | NULL | - | CHECK: 'YES' or 'NO' | Whether a follow-up meeting is needed |
| pricing | text | NULL | - | - | Pricing information discussed |
| decision_maker | text | NULL | - | CHECK: 'YES' or 'NO' | Whether decision maker was present |
| demo_provided | text | NULL | - | CHECK: 'YES' or 'NO' | Whether a demo was provided |

**Relationships**:
- Many-to-one with auth.users (created_by → auth.users.id)
- Many-to-one with contacts (contact_id → contacts.id)
- Many-to-one with companies (company_id → companies.id)

### notes

**Purpose**: Stores general notes and comments associated with various entities in the CRM.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the note |
| title | text | NULL | - | - | Note title or subject |
| content | text | NULL | - | - | Note content or body |
| company_id | uuid | NULL | - | FOREIGN KEY → companies(id) | Associated company |
| contact_id | uuid | NULL | - | FOREIGN KEY → contacts(id) | Associated contact |
| deal_id | uuid | NULL | - | FOREIGN KEY → deals(id) | Associated deal |
| user_id | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who created the note |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |
| note_type | text | NULL | 'general' | - | Type or category of note |
| author_id | uuid | NULL | - | FOREIGN KEY → auth.users(id) | Note author (may differ from creator) |
| pinned | boolean | NULL | false | - | Whether the note is pinned for visibility |
| organization_id | uuid | NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |

**Relationships**:
- Many-to-one with companies (company_id → companies.id)
- Many-to-one with contacts (contact_id → contacts.id)
- Many-to-one with deals (deal_id → deals.id)
- Many-to-one with auth.users (user_id → auth.users.id)
- Many-to-one with auth.users (author_id → auth.users.id)

### projects

**Purpose**: Manages project information and integration with external project management tools.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the project |
| name | text | NULL | - | - | Project name |
| status | text | NULL | 'active' | - | Current project status |
| listID | text | NULL | - | - | External list identifier (e.g., Trello) |
| cardListID | text | NULL | - | - | External card list identifier |
| cardID | text | NULL | - | - | External card identifier |
| organization_id | uuid | NULL | '00000000-0000-0000-0000-000000000001' | - | Organization/tenant identifier |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |
| listName | text | NULL | - | - | External list name |

**Relationships**:
- One-to-many with user_starred_projects (id ← user_starred_projects.project_card_id) [via text field]


### role_audit_log

**Purpose**: Maintains an audit trail of user role changes for security and compliance.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the audit entry |
| user_id | uuid | NOT NULL | - | FOREIGN KEY → auth.users(id) | User whose role was changed |
| old_role | USER-DEFINED | NULL | - | - | Previous role assignment |
| new_role | USER-DEFINED | NULL | - | - | New role assignment |
| changed_by | uuid | NOT NULL | - | FOREIGN KEY → auth.users(id) | User who made the role change |
| reason | text | NOT NULL | - | - | Reason for the role change |
| created_at | timestamp with time zone | NULL | now() | - | When the change occurred |

**Relationships**:
- Many-to-one with auth.users (user_id → auth.users.id)
- Many-to-one with auth.users (changed_by → auth.users.id)

### trello_cards

**Purpose**: Stores Trello card information for project management integration.

**Primary Key**: id (bigint)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | bigint | NOT NULL | GENERATED ALWAYS AS IDENTITY | PRIMARY KEY | Auto-incrementing identifier |
| cardName | text | NULL | - | - | Name of the Trello card |
| idList | text | NULL | - | - | Trello list identifier |
| cardID | text | NULL | - | - | Trello card identifier |
| card_created_at | text | NULL | - | - | Card creation timestamp (stored as text) |
| moved_to_list_at | text | NULL | - | - | When card was moved to current list |

**Relationships**:
- Many-to-one with trello_lists (idList → trello_lists.listID) [implied]

### trello_lists

**Purpose**: Stores Trello list information for project management integration.

**Primary Key**: id (bigint)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | bigint | NOT NULL | GENERATED ALWAYS AS IDENTITY | PRIMARY KEY | Auto-incrementing identifier |
| listID | text | NOT NULL | - | - | Trello list identifier |
| listName | text | NULL | - | - | Name of the Trello list |

**Relationships**:
- One-to-many with trello_cards (listID ← trello_cards.idList) [implied]

### user_integrations

**Purpose**: Manages third-party service integrations for individual users.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the integration |
| user_id | uuid | NOT NULL | - | FOREIGN KEY → auth.users(id) | User who owns the integration |
| integration_type | text | NOT NULL | - | - | Type of integration (e.g., Google, Slack) |
| access_token | text | NOT NULL | - | - | OAuth access token |
| refresh_token | text | NULL | - | - | OAuth refresh token |
| token_expires_at | timestamp with time zone | NULL | - | - | When the access token expires |
| is_active | boolean | NOT NULL | true | - | Whether the integration is active |
| created_at | timestamp with time zone | NOT NULL | now() | - | Integration setup timestamp |
| updated_at | timestamp with time zone | NOT NULL | now() | - | Record last update timestamp |

**Relationships**:
- Many-to-one with auth.users (user_id → auth.users.id)

### user_profiles

**Purpose**: Extends user information beyond the basic authentication data.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | - | PRIMARY KEY, FOREIGN KEY → auth.users(id) | User identifier (matches auth.users.id) |
| full_name | text | NULL | - | - | User's full name |
| created_at | timestamp with time zone | NULL | now() | - | Profile creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Profile last update timestamp |
| first_name | text | NULL | - | - | User's first name |
| last_name | text | NULL | - | - | User's last name |

**Relationships**:
- One-to-one with auth.users (id → auth.users.id)
- One-to-many with contacts (id ← contacts.owner_id)
- One-to-many with deals (id ← deals.assigned_to)

### user_roles

**Purpose**: Manages role assignments for users within the system.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the role assignment |
| user_id | uuid | NOT NULL | - | FOREIGN KEY → auth.users(id) | User receiving the role |
| role | USER-DEFINED | NOT NULL | 'user'::app_role | - | Role type assigned to user |
| assigned_by | uuid | NULL | - | FOREIGN KEY → auth.users(id) | User who assigned the role |
| assigned_at | timestamp with time zone | NULL | now() | - | When the role was assigned |
| created_at | timestamp with time zone | NULL | now() | - | Record creation timestamp |
| updated_at | timestamp with time zone | NULL | now() | - | Record last update timestamp |

**Relationships**:
- Many-to-one with auth.users (user_id → auth.users.id)
- Many-to-one with auth.users (assigned_by → auth.users.id)

### user_starred_projects

**Purpose**: Tracks which projects users have marked as favorites or starred.

**Primary Key**: id (uuid)

| Column Name | Data Type | Nullable | Default Value | Constraints | Description |
|-------------|-----------|----------|---------------|-------------|-------------|
| id | uuid | NOT NULL | gen_random_uuid() | PRIMARY KEY | Unique identifier for the starred relationship |
| user_id | uuid | NOT NULL | - | FOREIGN KEY → auth.users(id) | User who starred the project |
| project_card_id | text | NOT NULL | - | - | Project card identifier (references external system) |
| created_at | timestamp with time zone | NOT NULL | now() | - | When the project was starred |

**Relationships**:
- Many-to-one with auth.users (user_id → auth.users.id)
- Many-to-one with projects (project_card_id → projects.cardID) [implied via text field]


## Data Types Reference

| Data Type | Description | Usage in Schema |
|-----------|-------------|-----------------|
| uuid | Universally Unique Identifier | Primary keys, foreign keys, user references |
| text | Variable-length character string | Names, descriptions, URLs, general text fields |
| timestamp with time zone | Date and time with timezone information | Creation timestamps, update timestamps, activity dates |
| numeric | Exact numeric type with precision | Financial amounts, revenue, deal values |
| boolean | True/false values | Flags like completed, favorited, is_active |
| bigint | Large integer | File sizes, auto-incrementing IDs |
| smallint | Small integer | Scores, ratings |
| date | Date without time | Closed dates, specific date fields |
| jsonb | Binary JSON data | Audit log values, flexible data storage |
| ARRAY | Array of values | Tags, attendees, changed fields |
| USER-DEFINED | Custom enumerated types | Roles (app_role type) |

## Constraint Types

### Primary Key Constraints
All tables use uuid primary keys with `gen_random_uuid()` default, except:
- `trello_cards.id` and `trello_lists.id` use `bigint GENERATED ALWAYS AS IDENTITY`

### Foreign Key Constraints
The schema maintains referential integrity through foreign key relationships:
- User references point to `auth.users(id)` (external authentication table)
- Cross-table relationships maintain data consistency
- Some foreign keys are implied but not explicitly defined in the schema

### Check Constraints
Several tables include check constraints for data validation:
- `meetings.follow_up_meeting`: Must be 'YES' or 'NO'
- `meetings.decision_maker`: Must be 'YES' or 'NO'  
- `meetings.demo_provided`: Must be 'YES' or 'NO'

### Default Value Constraints
Common default patterns:
- `created_at` and `updated_at`: `now()`
- Boolean flags: `false`
- Status fields: Appropriate default status
- `organization_id`: Default organization UUID

## Entity Relationship Summary

### Core Business Entities
1. **Companies** → Central entity for organizations
2. **Contacts** → Individuals associated with companies
3. **Deals** → Sales opportunities linked to companies and contacts
4. **Activities** → Interactions and tasks across all entities

### Supporting Entities
1. **Attachments** → File storage for companies, contacts, and deals
2. **Notes** → General commentary system
3. **Meetings** → Meeting records with AI insights
4. **Projects** → Project management integration

### System Entities
1. **User Management** → Profiles, roles, integrations
2. **Audit Logs** → Change tracking for deals and roles
3. **External Integrations** → Trello synchronization

### Key Relationships
- **Many-to-Many**: Deals ↔ Contacts (via deal_contacts)
- **One-to-Many**: Companies → Contacts, Deals, Activities
- **Hierarchical**: Users → User Profiles → Role Assignments
- **Audit Trail**: Deals → Deal Audit Log, Users → Role Audit Log

## Multi-Tenancy
The schema implements organization-level multi-tenancy through:
- `organization_id` field in most tables
- Default organization: `'00000000-0000-0000-0000-000000000001'`
- Tenant isolation for data security

## External System Integration
- **Authentication**: References `auth.users` table (external)
- **Trello**: Dedicated tables for project management sync
- **Google Workspace**: Integration fields in companies table
- **Marketing Attribution**: UTM tracking in contacts table

## Notes
- This schema appears to be from a Supabase or similar PostgreSQL-based system
- Some foreign key constraints may be enforced at the application level
- The schema includes both normalized and denormalized data patterns
- Audit logging is implemented for critical business entities


```
