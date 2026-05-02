# Microsoft Sharepoint

Use a **Microsoft Entra ID App Registration** with **application permissions** and the **client credentials flow**. This lets your backend or automation access SharePoint without a user logging in.

For security, prefer:

```
Microsoft Graph → Application permission → Sites.Selected
```

Then grant that app access only to the SharePoint site(s) it needs. `Sites.Selected` is Microsoft’s scoped permission model for giving an app access to specific SharePoint site collections instead of the whole tenant. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/permissions-selected-overview?utm_source=chatgpt.com))

Avoid tenant-wide permissions like `Files.ReadWrite.All` or `Sites.ReadWrite.All` unless you truly want the app to read/write across all SharePoint sites.

***

## 1. Create the Entra ID app registration

In Microsoft 365 admin / Azure portal:

1. Go to **Microsoft Entra admin center**
2. Open **Identity → Applications → App registrations**
3. Click **New registration**
4. Name it something like:

```
SharePoint API File Manager
```

5. Supported account type:

```
Accounts in this organizational directory only
```

6. Click **Register**
7. Copy these values:
   * **Application / Client ID**
   * **Directory / Tenant ID**

Microsoft’s client credentials flow is designed for service-to-service access where the app authenticates with its own credentials rather than as a signed-in user. ([Microsoft Learn](https://learn.microsoft.com/en-us/entra/identity-platform/v2-oauth2-client-creds-grant-flow?utm_source=chatgpt.com))

***

## 2. Create a client secret or certificate

In the app registration:

1. Go to **Certificates & secrets**
2. Prefer **Certificates** for production
3. For quick setup, use **Client secrets → New client secret**
4. Set an expiration
5. Copy the secret value immediately

You will need:

```
TENANT_ID
CLIENT_ID
CLIENT_SECRET
```

For production, store the secret in a vault, not in code or environment files committed to source control.

***

## 3. Add Microsoft Graph API permissions

In the app registration:

1. Go to **API permissions**
2. Click **Add a permission**
3. Choose **Microsoft Graph**
4. Choose **Application permissions**
5. Add:

```
Sites.Selected
```

6. Click **Grant admin consent**

Important: `Sites.Selected` alone does **not** give access to any site. It only allows the app to be granted access to specific sites. You must do the site-level grant next. Microsoft describes `Sites.Selected` as managing application access at the site collection level. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/permissions-selected-overview?utm_source=chatgpt.com))

***

## 4. Get the SharePoint site ID

Use Microsoft Graph to resolve the SharePoint site.

Example site URL:

```
https://contoso.sharepoint.com/sites/Operations
```

Graph request:

```http
GET https://graph.microsoft.com/v1.0/sites/contoso.sharepoint.com:/sites/Operations
Authorization: Bearer {access_token}
```

Microsoft Graph supports retrieving a SharePoint site by hostname and server-relative path. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/site-getbypath?view=graph-rest-1.0\&utm_source=chatgpt.com))

The response will include an `id` like:

```
contoso.sharepoint.com,abc123-def456,ghi789-jkl012
```

Save that as:

```
SITE_ID
```

***

## 5. Grant the app write access to that site

Use an admin account or an admin-authorized app to grant your app access to the specific site.

Graph request:

```http
POST https://graph.microsoft.com/v1.0/sites/{SITE_ID}/permissions
Authorization: Bearer {admin_access_token}
Content-Type: application/json
```

Body:

```json
{
  "roles": ["write"],
  "grantedToIdentities": [
    {
      "application": {
        "id": "YOUR_CLIENT_ID",
        "displayName": "SharePoint API File Manager"
      }
    }
  ]
}
```

Use:

```
roles: ["read"]   // read only
roles: ["write"]  // add, edit, delete files/folders depending on library permissions
```

After this, your app can access only the selected site.

***

## 6. Get an app-only access token

Use the OAuth client credentials flow:

```bash
curl -X POST "https://login.microsoftonline.com/{TENANT_ID}/oauth2/v2.0/token" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "client_id={CLIENT_ID}" \
  -d "client_secret={CLIENT_SECRET}" \
  -d "scope=https://graph.microsoft.com/.default" \
  -d "grant_type=client_credentials"
```

Response:

```json
{
  "access_token": "eyJ...",
  "token_type": "Bearer",
  "expires_in": 3599
}
```

Use that token in Graph calls:

```http
Authorization: Bearer {access_token}
```

***

## 7. Find the document library / drive

In Graph, a SharePoint document library is represented as a **drive**. Microsoft Graph uses `drive` for the library and `driveItem` for files/folders. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/onedrive?view=graph-rest-1.0\&utm_source=chatgpt.com))

List document libraries for the site:

```http
GET https://graph.microsoft.com/v1.0/sites/{SITE_ID}/drives
Authorization: Bearer {access_token}
```

Microsoft documents this as:

```http
GET /sites/{siteId}/drives
```

for listing a site’s document libraries. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/drive-list?view=graph-rest-1.0\&utm_source=chatgpt.com))

Find the library named something like:

```
Documents
Shared Documents
Client Files
```

Save its ID as:

```
DRIVE_ID
```

***

## 8. Create a folder

Create a folder at the root of the document library:

```http
POST https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/root/children
Authorization: Bearer {access_token}
Content-Type: application/json
```

Body:

```json
{
  "name": "New Folder",
  "folder": {},
  "@microsoft.graph.conflictBehavior": "rename"
}
```

Create a folder inside another folder by path:

```http
POST https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/root:/Parent Folder:/children
Authorization: Bearer {access_token}
Content-Type: application/json
```

Body:

```json
{
  "name": "Child Folder",
  "folder": {},
  "@microsoft.graph.conflictBehavior": "rename"
}
```

Microsoft’s create-folder API creates a new folder or DriveItem under a parent item or path. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/driveitem-post-children?view=graph-rest-1.0\&utm_source=chatgpt.com))

***

## 9. Upload or replace a file

For files up to **250 MB**, use a simple upload:

```http
PUT https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/root:/Folder/FileName.pdf:/content
Authorization: Bearer {access_token}
Content-Type: application/pdf

{binary file content}
```

This creates the file if it does not exist, or replaces it if it does. Microsoft’s small file upload endpoint supports creating or updating file contents in one API call up to 250 MB. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/driveitem-put-content?view=graph-rest-1.0\&utm_source=chatgpt.com))

Example with `curl`:

```bash
curl -X PUT \
  "https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/root:/New Folder/test.txt:/content" \
  -H "Authorization: Bearer {ACCESS_TOKEN}" \
  -H "Content-Type: text/plain" \
  --data-binary "@test.txt"
```

For files larger than 250 MB, use Microsoft Graph’s upload session flow instead of simple upload. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/driveitem-put-content?view=graph-rest-1.0\&utm_source=chatgpt.com))

***

## 10. List folder contents

Root folder:

```http
GET https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/root/children
Authorization: Bearer {access_token}
```

Specific folder path:

```http
GET https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/root:/Folder Name:/children
Authorization: Bearer {access_token}
```

Microsoft Graph exposes folder contents through the DriveItem `children` relationship. ([Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/driveitem-list-children?view=graph-rest-1.0\&utm_source=chatgpt.com))

***

## 11. Rename or move files/folders

Rename a file or folder:

```http
PATCH https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/items/{ITEM_ID}
Authorization: Bearer {access_token}
Content-Type: application/json
```

Body:

```json
{
  "name": "New Name.pdf"
}
```

Move a file/folder to another parent folder:

```json
{
  "parentReference": {
    "id": "DESTINATION_FOLDER_ITEM_ID"
  },
  "name": "New Name.pdf"
}
```

***

## 12. Delete files/folders

```http
DELETE https://graph.microsoft.com/v1.0/drives/{DRIVE_ID}/items/{ITEM_ID}
Authorization: Bearer {access_token}
```

***

## Minimum permission recommendation

Use this for production:

```
Microsoft Graph Application Permission:
- Sites.Selected

Then grant site-specific role:
- write
```

Only use these broader permissions when necessary:

```
Files.ReadWrite.All
Sites.ReadWrite.All
```

Those are easier to configure but much riskier because they can allow broad tenant-wide SharePoint/OneDrive access.

***

## Environment variables to store

```bash
M365_TENANT_ID="..."
M365_CLIENT_ID="..."
M365_CLIENT_SECRET="..."
SHAREPOINT_HOSTNAME="contoso.sharepoint.com"
SHAREPOINT_SITE_PATH="/sites/Operations"
SHAREPOINT_SITE_ID="..."
SHAREPOINT_DRIVE_ID="..."
```

***

## Quick validation sequence

Run these in order:

```http
POST /{tenant}/oauth2/v2.0/token
GET  /sites/{hostname}:/sites/{siteName}
GET  /sites/{siteId}/drives
GET  /drives/{driveId}/root/children
POST /drives/{driveId}/root/children
PUT  /drives/{driveId}/root:/Test Folder/test.txt:/content
```

If all pass, the app is correctly set up to add/edit SharePoint files and folders.
