# Microsoft Dynamics 365 Setup

### Raia Platform Integration Guide: Microsoft Dynamics 365 CRM

This playbook provides step-by-step instructions for integrating the Raia platform with Microsoft Dynamics 365 CRM. The integration utilizes the Microsoft Entra ID (formerly Azure Active Directory) OAuth 2.0 client credentials flow. This is the recommended approach for server-to-server (S2S) communication, allowing the Raia platform to authenticate securely as a confidential client application and interact with the Dynamics 365 Web API without requiring interactive user login.

### 1. Register the Application in Microsoft Entra ID

The first step is to register the Raia platform as an application within the client's Microsoft Entra ID tenant. This establishes the identity of the application.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) using an account with administrator permissions in the same tenant as the Dynamics 365 environment \[1].
2. Navigate to **Identity** > **Applications** > **App registrations**.
3. Select **+ New registration**.
4. Provide a meaningful name for the application, such as "Raia Platform Integration".
5. Under **Supported account types**, select **Accounts in this organizational directory only (Single tenant)** \[1].
6. Leave the **Redirect URI** blank, as it is not required for the client credentials flow.
7. Click **Register** to create the application.

Once registered, navigate to the **Overview** page of the newly created app and record the **Application (client) ID** and the **Directory (tenant) ID**. These values are essential for configuring the authentication flow \[1].

**Important Note on API Permissions:** For true Server-to-Server (S2S) authentication using the client credentials flow, **you do not need to configure delegated API permissions** (such as `user_impersonation`) \[1] \[2]. The application will authenticate as itself, and its authorization will be governed entirely by the Application User and Security Roles configured inside Dynamics 365 (see Step 3).

### 2. Configure Application Credentials (Certificates Preferred)

To prove its identity when requesting an access token, the application requires credentials. Microsoft strongly recommends using certificate credentials or managed identities over password credentials (client secrets) for confidential client applications \[3].

#### Option A: Upload a Certificate (Recommended)

1. In the left navigation pane of the app registration, select **Certificates & secrets**.
2. Under the **Certificates** tab, click **Upload certificate** \[2].
3. Select your public key certificate file (`.cer`, `.pem`, or `.crt`).
4. Provide a description and click **Add**.
5. The Raia platform will use the corresponding private key to sign the token requests.

#### Option B: Generate a Client Secret (Alternative)

If certificates or managed identities cannot be used, you can generate a client secret.

1. Under the **Client secrets** tab, click **+ New client secret** \[1].
2. Provide a description and select an appropriate expiration period.
3. Click **Add**.
4. **Critical:** Immediately copy the **Value** of the newly created client secret and store it securely in a key vault. This value will not be displayed again once you navigate away from the page \[2].

### 3. Create an Application User in Dynamics 365

To allow the registered application to interact with Dynamics 365 data, you must create an "Application User" within the Dynamics 365 environment and assign it the necessary security roles. This binds the Entra ID app registration to a specific identity inside Dataverse \[1] \[2].

1. Log in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. Select **Environments** in the left navigation pane and choose the target Dynamics 365 environment.
3. Navigate to **Settings** > **Users + permissions** > **Application users**.
4. Click **+ New app user**.
5. Click **+ Add an app** and search for the application you registered in Microsoft Entra ID. Select it and click **Add**.
6. Select the appropriate **Business unit** for the application user.
7. Click the pencil icon next to **Security roles** to assign permissions.
8. **Least Privilege Principle:** Select a custom security role that provides the minimum required permissions for the Raia platform to function (e.g., Read/Write access only to Contacts, Leads, and Opportunities). Do not assign the System Administrator role.
9. Click **Save** and then **Create** to finalize the application user.

### 4. Authenticate and Connect

With the application registered and the user created, the Raia platform can now authenticate and make requests to the Dynamics 365 Web API.

#### Obtaining an Access Token

The Raia platform must request an OAuth 2.0 access token from the Microsoft identity platform token endpoint using the client credentials flow.

Make a `POST` request to the following URL: `https://login.microsoftonline.com/{tenant_id}/oauth2/v2.0/token`

Include the following parameters in the request body (application/x-www-form-urlencoded):

| Parameter       | Value                                                                                                                                                                            |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `client_id`     | The Application (client) ID obtained in Step 1.                                                                                                                                  |
| `client_secret` | The client secret value obtained in Step 2 (if using secrets). If using certificates, use `client_assertion_type` and `client_assertion` instead.                                |
| `scope`         | The Dynamics 365 environment URL appended with `/.default` (e.g., `https://orgname.crm.dynamics.com/.default`). This is the required scope format for confidential clients \[2]. |
| `grant_type`    | `client_credentials`                                                                                                                                                             |

The response will contain an `access_token`, which is typically valid for 60 minutes.

#### Making API Requests

Use the obtained access token to authenticate requests to the Dynamics 365 Web API. Include the token in the `Authorization` header of your HTTP requests as a Bearer token.

The base URL for the Web API typically follows this format: `https://{organization_name}.api.crm.dynamics.com/api/data/v9.2/`

**Example: Retrieving Contacts**

```http
GET https://{organization_name}.api.crm.dynamics.com/api/data/v9.2/contacts
Authorization: Bearer {access_token}
OData-MaxVersion: 4.0
OData-Version: 4.0
Accept: application/json
```

### 5. Validation and Operational Security

Before deploying the integration to production, perform the following validation and operational security steps:

#### Validation Steps

1. **Test Token Acquisition:** Ensure the Raia platform can successfully acquire an access token using the configured credentials.
2. **Call the WhoAmI Endpoint:** Make a `GET` request to `https://{organization_name}.api.crm.dynamics.com/api/data/v9.2/WhoAmI` to verify the token is accepted and correctly identifies the Application User.
3. **Test Least Privilege:** Attempt to perform CRUD operations on tables the Raia platform _should_ have access to, and verify that operations on unauthorized tables are correctly rejected (returning a 403 Forbidden).

#### Operational Security Best Practices

* **Credential Rotation:** Establish a schedule to rotate certificates or client secrets before they expire to prevent integration downtime.
* **Secure Storage:** Never hardcode credentials. Store certificates or client secrets in a secure vault (e.g., Azure Key Vault, AWS Key Management Service).
* **Environment Isolation:** Create separate Entra ID app registrations and Dynamics 365 Application Users for Development, Testing, and Production environments.

### References

\[1] Microsoft Learn. "Use single-tenant server-to-server authentication". https://learn.microsoft.com/en-us/power-apps/developer/data-platform/use-single-tenant-server-server-authentication \[2] Microsoft Learn. "Use OAuth authentication with Microsoft Dataverse". https://learn.microsoft.com/en-us/power-apps/developer/data-platform/authenticate-oauth \[3] Microsoft Learn. "Best practices for the Microsoft identity platform". https://learn.microsoft.com/en-us/entra/identity-platform/identity-platform-integration-checklist
