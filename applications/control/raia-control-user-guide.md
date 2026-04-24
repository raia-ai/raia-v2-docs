# raia Control User Guide

***

### Command Deck

> Your home base for monitoring and managing AI outreach missions.

#### Overview

The **Command Deck** is the main dashboard of raia Control. It provides an at-a-glance view of your outreach operations and quick access to key actions.

#### Dashboard Stats

The Command Deck displays three key metrics:

* **Active Missions** — The number of campaigns currently running and sending messages to contacts.
* **Agents** — The total number of AI Agents available for deployment across your account.
* **Total Contacts** — The total number of contacts in your database.

#### Setup Alerts

If no AI Agents are connected, the Command Deck displays a prominent warning banner directing you to **Settings → Agents** to add your first agent. This ensures you're ready to launch missions.

#### Recent Missions

The dashboard shows your most recent missions with the following details for each:

* **Mission Name** — The name you assigned when creating the mission.
* **Status Badge** — Color-coded status indicator:
  * 🟢 **Active** — Currently sending messages
  * 🔵 **Scheduled** — Waiting for the scheduled send time
  * 🟣 **Completed** — All messages sent
  * ⚪ **Draft** — Created but not yet launched
  * 🔴 **Failed** — Mission encountered an error
* **Agent** — Which AI Agent is assigned to the mission.
* **Date** — When the mission was scheduled or started.
* **Channel** — The communication channel (Email, SMS, or Voice), shown as a colored badge.
* **Progress Bar** — Visual indicator showing how many messages have been sent out of the total (e.g., "45 / 100").

#### Quick Actions

From the Command Deck you can:

* Click **View All Missions** to navigate to the full Missions page.
* Click **Launch New Mission** to start creating a new outreach campaign.
* Click on any recent mission card to view its detailed report.

***

### Quick Tips

* **Use context for better personalization** — Add Apollo or Company context to your contacts for more relevant AI-generated messages.
* **Test before you send** — Always use the Test Mission feature to preview AI messages before launching.
* **Monitor engagement scores** — Check the Conversations page regularly to identify and follow up with engaged leads.
* **Organize with lists** — Keep contacts organized in lists for easier mission targeting and tracking.

***

### Getting Started

> Learn the basics of setting up your account and launching your first mission.

#### What is raia Control?

raia Control is an AI-powered outreach platform that helps you convert more leads through personalized, intelligent conversations. It connects to AI Agents on the Raia platform to automate and personalize your outbound marketing campaigns via email and SMS.

#### How do I set up my first AI Agent?

To set up your first AI Agent:

1. Go to **Settings** → **Agents** tab
2. Click **Add Agent**
3. Enter your Agent's name and the API key from the Raia platform
4. Optionally add a description and phone number for SMS
5. Click **Save**

Once connected, your agent will be available when creating missions.

#### What do I need before launching a mission?

Before launching your first mission, you'll need:

1. **An AI Agent** - Connected from the Raia platform
2. **Contacts** - Uploaded via CSV or added manually
3. **A clear goal** - What do you want to achieve with this outreach?

Once you have these, you're ready to launch!

#### How do I navigate the dashboard?

The **Command Deck** is your home base. From here you can:

* View mission statistics and recent activity
* See conversation engagement scores
* Quick-launch new missions
* Access all main sections via the sidebar

The sidebar menu includes: Command Deck, Launch Mission, Missions, Conversations, Contacts, and Settings.

***

### Managing Contacts

> Learn how to import, organize, and manage your contact database.

#### How do I upload contacts?

To upload contacts:

1. Go to **Contacts** page
2. Click the **Upload Contacts** button
3. Upload a CSV file with your contact data
4. Map your CSV columns to contact fields (first name, last name, email, phone, etc.)
5. Optionally add context fields for personalization
6. Assign tags and lists to organize your contacts
7. Click **Upload** to complete

#### What fields can I include in my CSV?

Your CSV can include:

**Required fields:**

* First Name
* Last Name

**Optional fields:**

* Email
* Phone
* Apollo Context (for AI personalization)
* Company Context
* Custom context fields
* Initial email subject/body
* Initial SMS message

#### How do I organize contacts with tags and lists?

**Tags** are labels you can apply to contacts (e.g., 'VIP', 'Hot Lead', 'Follow-up').

**Lists** are collections of contacts (e.g., 'Q1 Prospects', 'Enterprise Clients').

To manage:

1. Select contacts using the checkbox
2. Use the **Add Tag** or **Add to List** buttons in the selection bar
3. You can also manage tags and lists in **Settings** → **Tags & Lists**

#### How do I verify email addresses?

Email verification uses ZeroBounce to validate email addresses:

1. Select the contacts you want to verify
2. Click **Verify Emails** in the selection bar
3. The system will check each email's validity
4. Results appear in the contact's profile with verification status

Note: You need a ZeroBounce API key configured in **Settings** → **Integrations**.

#### What does the 'Unlisted' view show?

The **Unlisted** view shows contacts that haven't been assigned to any list. This helps you identify contacts that may need organizing or were recently uploaded without list assignment.

***

### Launching Missions

> Everything you need to know about creating and managing outreach campaigns.

#### What is a Mission?

A **Mission** is an outreach campaign that uses your AI Agent to engage with a set of contacts. Missions can be sent via Email or SMS and support different message strategies:

* **AI-Generated**: Personalized messages created by your AI Agent
* **Standard**: A single message template sent to all contacts
* **Contact-Specific**: Pre-written messages stored on each contact

#### How do I create a new mission?

To create a mission:

1. Click **Launch Mission** in the sidebar
2. **Define** your mission name and objective prompt
3. **Select Agent** - Choose which AI Agent to use
4. **Choose Channel** - Email or SMS
5. **Select Contacts** - Pick from lists or individual contacts
6. **Configure Messages** - Choose strategy and set templates
7. **Set Schedule** - Send immediately or schedule for later
8. **Review & Launch**

#### What's the difference between message strategies?

**AI-Generated Messages:** Your AI Agent creates unique, personalized messages for each contact based on their context and your mission prompt.

**Standard Message:** One message template sent to all contacts. Good for announcements or when personalization isn't needed.

**Contact-Specific Messages:** Uses the initial message already saved on each contact record. Useful when you've pre-written messages during import.

#### How do I pause or cancel a mission?

From the **Missions** page or Mission Detail view:

* **Pause**: Temporarily stops sending. You can resume later.
* **Cancel**: Permanently stops the mission. Cannot be resumed.
* **Archive**: Hides completed or cancelled missions from the main view.

Note: Messages already sent cannot be recalled.

#### What do the mission statuses mean?

* **Draft**: Mission created but not yet launched
* **Scheduled**: Waiting for the scheduled send time
* **Active**: Currently sending messages
* **Paused**: Temporarily stopped, can be resumed
* **Completed**: All messages sent
* **Cancelled**: Permanently stopped before completion

***

### Conversations & Engagement

> Track and manage AI-powered conversations with your contacts.

#### How do I view conversations?

Go to **Conversations** in the sidebar to see all AI conversations:

* Filter by mission, status, or search by contact name
* Click any conversation to see the full message history
* View engagement scores to identify hot leads
* See when contacts opened, clicked, or replied

#### What is the Engagement Score?

The **Engagement Score** (1-10) indicates how interested a contact appears based on their conversation. Higher scores suggest:

* Active participation in the conversation
* Positive responses to your outreach
* Potential buying signals

Use this to prioritize follow-ups with the most engaged leads.

#### How do I track opens, clicks, and replies?

Each contact in a mission has tracking indicators:

* **Opened**: Contact opened your email (📧)
* **Clicked**: Contact clicked a link (🔗)
* **Replied**: Contact responded (💬)

View these in the Mission Detail page or Conversations list.

#### Can I see the AI-generated messages before they're sent?

Yes! When creating a mission with AI-generated messages:

1. Complete the mission setup
2. Before launching, use **Test Mission** to preview generated messages
3. Review the AI's output for several sample contacts
4. Adjust your prompt if needed before sending

***

### AI Agents

> Configure and manage your AI Agents from the Raia platform.

#### What is an AI Agent?

An **AI Agent** is a trained AI model on the Raia platform that handles conversations on your behalf. Each agent has:

* A unique personality and communication style
* Knowledge about your business
* Ability to answer questions and engage leads
* An API key for integration

#### How do I connect an AI Agent?

1. Create an agent on the Raia platform (raia.ai)
2. Copy the API key from your Raia dashboard
3. In raia Control, go to **Settings** → **Agents**
4. Click **Add Agent**
5. Paste your API key and save

Your agent is now ready to use in missions!

#### Can I share agents with team members?

Yes! Agent owners can share agents with team members:

1. Go to **Settings** → **Agents**
2. Click the share icon on an agent
3. Enter the team member's email
4. They'll receive access to use that agent in their missions

#### How do I test my agent?

In **Settings** → **Agents**, each agent has a **Test** button:

1. Click Test on your agent
2. Enter a sample message as if you were a lead
3. See how your agent responds
4. Refine your agent's training on Raia if needed

***

### Settings & Configuration

> Customize your account, team, and integration settings.

#### How do I invite team members?

Go to **Settings** → **Team**:

1. Click **Invite Member**
2. Enter their email address
3. Select their role (Member or Admin)
4. Click **Send Invitation**

They'll receive an email to join your account and can access shared resources.

#### How do I set up integrations?

Go to **Settings** → **Integrations** to configure:

* **Apollo.io**: For contact enrichment
* **ZeroBounce**: For email verification

Enter your API keys and test the connection before saving.

#### Can I customize branding?

Yes! Go to **Settings** → **Branding**:

* Upload your company logo
* Set a custom brand name
* Configure marketing display name

This branding appears in the sidebar and on your login page.

#### How do I manage templates?

**Templates** are reusable message formats for missions:

1. Go to **Settings** → **Templates** or the **Templates** page
2. Create templates with placeholders like \{{first\_name\}}
3. Use templates when configuring mission messages
4. Save time by reusing proven message formats

#### How do I track email opens, clicks, and deliveries?

Email tracking requires webhook integration with your email provider:

**To enable tracking:** Contact your administrator to set up the appropriate webhooks in Mailgun. Once configured, the system will automatically track:

* **Delivered At**: When your email was successfully delivered
* **Opened At**: When the recipient opened your email
* **Clicked At**: When the recipient clicked a link

Tracking data will appear in the Mission Detail page under the Total Contacts section.

***

### Still need help?

Can't find what you're looking for? Contact our support team for personalized assistance.

📧 **support@raiaai.com**
