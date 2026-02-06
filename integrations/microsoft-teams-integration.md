# Microsoft Teams Integration

## Build an Azure Bot That Connects to a raia Agent in Microsoft Teams

Got it — here’s the cleaned-up, well-structured **Markdown version** of the document you uploaded. I’ve preserved the technical details, clarified headings, and formatted code blocks properly for easy reuse in docs, README files, or internal guides.

{% file src="../.gitbook/assets/app-package.zip" %}

***

## Azure Bot & Workflow Configuration

### Create Azure Bot

1. **Create an Azure Bot**
   * Type of App: **Single Tenant**
   * Create a **new Microsoft App ID**
2. Navigate to:
   * **Azure Bot → Settings → Configuration**
3. Copy the **App Tenant ID**
4. Open **n8n**
5. Create a **POST Webhook**
   * Name it: `Webhook`
   * Configure it to **respond immediately**
6. Add an **IF node**
   *   Condition:

       ```
       {{ $json.body.type }} == "message"
       ```
7. On the **TRUE** path, add an **HTTP Request** node to get an OAuth token:
   * **Method:** POST
   *   **URL:**

       ```
       https://login.microsoftonline.com/{APP_TENANT_ID}/oauth2/v2.0/token
       ```
   * **Authentication:** None
   *   **Send Body:** Form URL Encoded (Using Fields Below)

       | Key            | Value                                                                          |
       | -------------- | ------------------------------------------------------------------------------ |
       | grant\_type    | client\_credentials                                                            |
       | client\_id     | {FROM OAUTH}                                                                   |
       | client\_secret | {FROM OAUTH}                                                                   |
       | scope          | [https://api.botframework.com/.default](https://api.botframework.com/.default) |
   * The response will return a **Bearer access token**
8. Add another **HTTP Request** node to send a message:
   * **Method:** POST
   *   **URL:**

       ```
       {{ $('Webhook').item.json.body.serviceUrl }}v3/conversations/{{ $('Webhook').item.json.body.conversation.id }}/activities
       ```
   * **Authentication:** None
   *   **Headers:**

       | Key           | Value                  |
       | ------------- | ---------------------- |
       | Authorization | Bearer {access\_token} |
       | Content-Type  | application/json       |
   * **Body:** JSON (see below)
9. Return to **Azure Bot → Settings → Configuration**
10. Set:
    * **Messaging Endpoint:** `{YOUR N8N WEBHOOK URL}`

***

### Message Payload (Fig. 1)

```json
{
  "type": "message",
  "from": {
    "id": "{{ $('Webhook').item.json.body.recipient.id }}",
    "name": "{{ $('Webhook').item.json.body.recipient.name }}"
  },
  "recipient": {
    "id": "{{ $('Webhook').item.json.body.from.id }}"
  },
  "conversation": {
    "id": "{{ $('Webhook').item.json.body.conversation.id }}"
  },
  "text": "Hello from raia."
}
```

***

### Create the Custom Teams App

1. Create `outline.png` (32×32 exactly)
2. Create `color.png` (192×192 exactly)
3. Create `manifest.json`
4.  Zip all three files into:

    ```
    app-package.zip
    ```

***

### Example `manifest.json`

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.17/MicrosoftTeams.schema.json",
  "manifestVersion": "1.17",
  "version": "1.0.0",
  "id": "886dfe00-189b-4b39-a9a7-94b5c518c769",
  "developer": {
    "name": "RAIA AI",
    "websiteUrl": "https://raiaai.com",
    "privacyUrl": "https://www.raiaai.com/raia-privacy-policy",
    "termsOfUseUrl": "https://www.raiaai.com/raia-terms-of-services"
  },
  "name": {
    "short": "RAIA Agent",
    "full": "RAIA Teams Agent"
  },
  "description": {
    "short": "Your AI-powered assistant for Teams.",
    "full": "RAIA is an intelligent bot that helps your team with various tasks and provides quick access to information."
  },
  "icons": {
    "outline": "outline.png",
    "color": "color.png"
  },
  "accentColor": "#FFFFFF",
  "bots": [
    {
      "botId": "886dfe00-189b-4b39-a9a7-94b5c518c769",
      "scopes": ["personal", "team", "groupChat"],
      "supportsFiles": false,
      "isNotificationOnly": false
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
    "raia.app.n8n.cloud"
  ]
}
```

***

### Upload the Custom App

#### 1. Enable Microsoft Teams Channel in Azure

* Open **Azure Portal**
* Navigate to your **Azure Bot resource**
* Go to **Settings → Channels**
* Select **Microsoft Teams**
* Accept the Terms of Service
* Ensure **Cloud Environment** is set to _Microsoft Teams Commercial_
* Click **Apply**
* Confirm the Teams channel shows a green checkmark

***

#### 2. Configure Teams Admin Center

* Sign in to **Teams Admin Center**
* Go to **Teams apps → Setup policies**
* Edit **Global (Org-wide default)** policy
* Enable **Upload custom apps**
* Go to **Teams apps → Manage apps**
* Enable **Let users interact with custom apps in preview**

***

#### 3. Sideload and Install the Bot

* Open **Microsoft Teams**
* Click **Apps**
* Select **Manage your apps**
* Click **Upload an app → Upload a custom app**
* Select `app-package.zip`
* Click **Add**
* Optionally install into:
  * A Team
  * A Channel
  * A Group Chat

***

### Test Your Bot in Teams

* **Personal Chat**
  * Send messages like `hello` or `help`
* **Team / Channel**
  * Use `@raia-teams-agent help`
* **Group Chat**
  * Add the bot and @mention it
* **Functionality**
  * Verify all core workflows behave correctly

