# Uploading a Client List

## 📇 Adding a Contact List

The **Contacts** section in Mission Control allows you to upload, organize, and manage your outreach lists. Each list represents a group of contacts that your AI Agent will reach out to during campaigns.

Adding a contact list is a simple step-by-step process designed to prepare your data for multi-channel campaigns across both **email** and **SMS**.

***

### 🧭 Step 1: Open the Contacts Tab

From the main sidebar, select **Contacts**.\
This is where you can upload and manage your contact databases.\
Click the **Upload Contacts** button to begin the process.

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-06 095740.png" alt=""><figcaption></figcaption></figure>

***

### 📂 Step 2: Assign Tags and Lists

You’ll be prompted to assign your upload to a list. Tags and lists help keep your contacts organized.

* **Tags** are labels for grouping contacts by campaign, product, or region.
* **Lists** represent specific upload groups that can be targeted in missions.

You can:

* Select an existing list.
* Or create a new one by checking **Create a new list** and entering a name.
* Optionally, create new tags to help filter or categorize your upload.

When ready, click **Next**.

<div align="center"><figure><img src="../../.gitbook/assets/Screenshot 2025-10-06 095837.png" alt="" width="563"><figcaption></figcaption></figure></div>

***

### 📤 Step 3: Upload Your CSV File

Upload your CSV file containing your contact data.\
Your file should include at least the following columns:

* **First Name**
* **Last Name**
* **Campaign or Channel**
* **Email** or **Phone Number** (depending on outreach type)
* **Email Body** (in HTML format for proper spacing and visuals)

Mission Control supports uploads of up to **10,000 rows per file**.

Once the upload completes, you’ll see the number of rows processed.\
Click **Next** to continue.

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-06 100957 (1).png" alt="" width="563"><figcaption></figcaption></figure>

***

### 🧩 Step 4: Map Your Fields

In this step, you’ll match your CSV columns to Mission Control’s contact fields.\
First and Last Name are required.

Typical field mappings include:

* **First Name** → First Name
* **Last Name** → Last Name
* **Email** → Email
* **Phone Number** → Phone Number

You can also configure **Optional Mappings** for:

* **SMS Message**
* **Email Subject**
* **Email Body**

This ensures Mission Control understands exactly what data to use for each communication channel.\
Click **Next** to continue.

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-06 095944.png" alt="" width="563"><figcaption></figcaption></figure>

***

### 🧠 Step 5: Map Context Data

Context data adds additional personalization or metadata to your contacts.\
You can choose from:

* **No Additional Context:** Only standard fields are used.
* **Use a Single Column for Context:** A single column (like “Notes” or “Campaign Info”) will be stored as plain text in the contact’s context.
* **Use Multiple Columns for Context:** The most detailed option, ideal for complex missions that use multiple variables.

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-06 100029.png" alt="" width="563"><figcaption></figcaption></figure>

***

### ✅ Step 6: Review and Confirm

Before finalizing your upload, Mission Control provides a confirmation screen with a **preview** of your data.\
Check the details carefully to ensure all fields are mapped correctly.

Once everything looks right, click **Upload** to complete the import.

Your contact list will now appear in the **Contacts** section, ready for use in your next Mission.

<figure><img src="../../.gitbook/assets/Screenshot 2025-10-06 100138.png" alt="" width="563"><figcaption></figcaption></figure>

***

### 💡 Best Practices

* Always double-check your CSV headers before uploading.
* Include HTML formatting in your **Email Body** column for better presentation.
* Use meaningful list and tag names to keep your campaigns organized.
* For SMS-only missions, make sure phone numbers include the country code.
