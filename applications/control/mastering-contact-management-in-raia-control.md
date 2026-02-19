# Mastering Contact Management in RAIA Control

Your contact database is the foundation of all your outreach activities. RAIA Control provides a comprehensive suite of tools to help you import, organize, and manage your contacts efficiently. This guide covers the core features of the **Contacts** section, which is your central hub for all contact-related activities.

### The Contact Data Model

A contact in RAIA Control is more than just an email address. It is a rich profile that stores essential information for personalized engagement. The key fields include:

<table data-header-hidden><thead><tr><th width="146.82421875"></th><th></th></tr></thead><tbody><tr><td><strong>Field</strong></td><td><strong>Description</strong></td></tr><tr><td>First Name</td><td>The contact's first name.</td></tr><tr><td>Last Name</td><td>The contact's last name.</td></tr><tr><td>Email</td><td>The primary email address, used as a key identifier for email missions.</td></tr><tr><td>Phone</td><td>The contact's phone number, used for SMS-based missions.</td></tr></tbody></table>

Beyond these, each contact has several other attributes that enable advanced segmentation and personalization:

* Source: Indicates how the contact was added (e.g., `CSV Import`, `Apollo`).
* Context: A flexible JSON field for storing custom, structured data for lead enhancement.
* Lists and Tags: For organizing contacts into broad groups and applying granular labels.
* Archive Status: Allows you to remove contacts from active views while preserving their data.

### Importing and Exporting Contacts

RAIA Control simplifies the process of getting contacts into and out of the platform.

#### Importing via CSV

The most common method for adding contacts in bulk is through a CSV file import.

1. **Prepare Your File:** Ensure your contact data is in a clean CSV file with clear column headers (e.g., `first_name`, `last_name`, `email`).
2. **Initiate Import:** In the **Contacts** section, click **"Import Contacts"**.
3. **Map Fields:** The system will prompt you to map the columns from your CSV to the corresponding fields in RAIA Control. This ensures your data is imported accurately.
4. **Assign to a List (Optional):** During the import process, you can choose to add all contacts from the file directly to a specific list, which is a great way to segment them from the start.

#### Exporting Contacts

You can also export your contact data from RAIA Control at any time. Simply select the contacts you wish to export (or select all) and use the export function to generate a CSV file.

### Managing Contacts with Bulk Actions

As your database grows, managing contacts one by one becomes inefficient. RAIA Control offers powerful bulk actions to streamline this process.

From the main contacts table, you can select multiple contacts using the checkboxes next to their names. Once selected, a menu of bulk actions will become available, allowing you to:

* **Add to List:** Assign multiple contacts to one or more lists simultaneously.
* **Apply Tags:** Add one or more tags to a group of contacts to categorize them.
* **Archive:** Move multiple contacts to the archive, cleaning up your active view without losing historical data.

By mastering these contact management features, you can maintain a clean, organized, and data-rich foundation for all your automated outreach campaigns in RAIA Control.
