# Microsoft Dynamics 365 Setup

### Raia Platform Integration Guide: Microsoft Dynamics 365 CRM

This playbook provides step-by-step instructions for integrating the Raia platform with Microsoft Dynamics 365 CRM. The integration utilizes the Microsoft Entra ID (formerly Azure Active Directory) OAuth 2.0 client credentials flow, which is the recommended approach for server-to-server (S2S) communication. This method allows the Raia platform to authenticate securely as an application and interact with the Dynamics 365 Web API to manage records such as contacts, leads, and opportunities.

### 1. Register the Application in Microsoft Entra ID

The first step in the integration process is to register the Raia platform as an application within the client's Microsoft Entra ID tenant. This registration establishes the identity of the application and allows it to request access tokens.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) or the Azure portal using an account with administrator permissions in the same tenant as the Dynamics 365 environment \[1].
2. Navigate to **Identity** > **Applications** > **App registrations**.
3. Select **+ New registration**.
4. Provide a meaningful name for the application, such as "Raia Platform Integration".
5. Under **Supported account types**, select **Accounts in this organizational directory only (Single tenant)**, as the integration is typically specific to the client's organization \[1].
6. Leave the **Redirect URI** blank, as it is not required for the client credentials flow.
7. Click **Register** to create the application.

Once the application is registered, navigate to the **Overview** page of the newly created app and record the **Application (client) ID** and the **Directory (tenant) ID**. These values are essential for configuring the authentication flow in the Raia platform \[1].

### 2. Configure API Permissions

After registering the application, you must grant it permission to access the Dynamics 365 API.

1. In the left navigation pane of the app registration, select **API permissions**.
2. Click **+ Add a permission**.
3. Select the **APIs my organization uses** tab and search for "Dataverse" or "Dynamics CRM" \[1].
4. Select the appropriate API from the search results.
5. Choose **Delegated permissions** and check the box for **user\_impersonation** \[1].
6. Click **Add permissions**.
7. Crucially, you must grant admin consent for these permissions. Click the **Grant admin consent for \[Organization Name]** button and confirm the action \[1]. This step ensures that the application can access the API without requiring individual user consent, which is necessary for background services.

### 3. Generate a Client Secret

The application requires a client secret to prove its identity when requesting an access token.

1. In the left navigation pane of the app registration, select **Certificates & secrets**.
2. Under the **Client secrets** tab, click **+ New client secret** \[2].
3. Provide a description for the secret (e.g., "Raia Integration Secret") and select an appropriate expiration period (e.g., 12 or 24 months).
4. Click **Add**.
5. **Important:** Immediately copy the **Value** of the newly created client secret and store it securely. This value will not be displayed again once you navigate away from the page \[2].

### 4. Create an Application User in Dynamics 365

To allow the registered application to interact with Dynamics 365 data, you must create an application user within the Dynamics 365 environment and assign it the necessary security roles.

1. Log in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. Select **Environments** in the left navigation pane and choose the target Dynamics 365 environment \[3].
3. Navigate to **Settings** > **Users + permissions** > **Application users** \[3].
4. Click **+ New app user**.
5. Click **+ Add an app** and search for the application you registered in Microsoft Entra ID. Select it and click **Add** \[3].
6. Select the appropriate **Business unit** for the application user.
7. Click the pencil icon next to **Security roles** to assign permissions.
8. Select a custom security role that provides the minimum required permissions for the Raia platform to function. Avoid assigning the System Administrator role unless absolutely necessary. A typical integration role should include Read and Write access to core entities such as Accounts, Contacts, Leads, and Opportunities \[4].
9. Click **Save** and then **Create** to finalize the application user \[3].

### 5. Authenticate and Connect

With the application registered and the user created, the Raia platform can now authenticate and make requests to the Dynamics 365 Web API.

#### Obtaining an Access Token

The Raia platform must request an OAuth 2.0 access token from the Microsoft identity platform token endpoint using the client credentials flow.

Make a `POST` request to the following URL: `https://login.microsoftonline.com/{tenant_id}/oauth2/v2.0/token`

Include the following parameters in the request body (application/x-www-form-urlencoded):

| Parameter       | Value                                                                                                           |
| --------------- | --------------------------------------------------------------------------------------------------------------- |
| `client_id`     | The Application (client) ID obtained in Step 1.                                                                 |
| `client_secret` | The client secret value obtained in Step 3.                                                                     |
| `scope`         | The Dynamics 365 environment URL appended with `/.default` (e.g., `https://orgname.crm.dynamics.com/.default`). |
| `grant_type`    | `client_credentials`                                                                                            |

The response will contain an `access_token`, which is typically valid for 60 minutes \[5].

#### Making API Requests

Use the obtained access token to authenticate requests to the Dynamics 365 Web API. Include the token in the `Authorization` header of your HTTP requests as a Bearer token.

The base URL for the Web API follows this format: `https://{organization_name}.api.crm.dynamics.com/api/data/v9.2/`

**Example: Retrieving Contacts**

To retrieve a list of contacts, make a `GET` request to the `contacts` endpoint:

```http
GET https://{organization_name}.api.crm.dynamics.com/api/data/v9.2/contacts
Authorization: Bearer {access_token}
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json
```

The Raia platform can utilize standard RESTful operations (GET, POST, PATCH, DELETE) to interact with various entities within Dynamics 365, enabling seamless data synchronization and agent-driven actions.

### References

\[1] Microsoft Learn. "Tutorial: Register an app with Microsoft Entra ID (Microsoft Dataverse)". https://learn.microsoft.com/en-us/power-apps/developer/data-platform/walkthrough-register-app-azure-active-directory \
\[2] ZappySys Blog. "How to register App for Dynamics CRM 365 / CDS / Dataverse API (Azure AD / OAuth)". https://zappysys.com/blog/register-app-dynamics-crm-365-cds-dataverse-api-azure-ad-oauth/ \
\[3] Microsoft Learn. "Create a Dataverse application user (preview)". https://learn.microsoft.com/en-us/power-platform/admin/create-dataverseapplicationuser \
\[4] Demandbase Help Center. "Step 2 (OAuth): Create Microsoft Dynamics Integration User". https://support.demandbase.com/hc/en-us/articles/10420777675675-Step-2-OAuth-Create-Microsoft-Dynamics-Integration-User \
\[5] Microsoft Learn. "OAuth 2.0 client credentials flow on the Microsoft identity platform". https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow
