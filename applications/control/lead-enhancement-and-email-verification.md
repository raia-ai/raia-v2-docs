# Lead Enhancement & Email Verification

Maintaining high-quality data is fundamental to the success of any outreach campaign. RAIA Control provides built-in tools and flexible architecture to help you verify contact information and enrich your leads with valuable data, ensuring better deliverability and enabling deeper personalization.

### Email Verification with ZeroBounce

Sending emails to invalid addresses can harm your sender reputation and lead to lower deliverability rates across the board. To combat this, RAIA Control integrates with ZeroBounce, a leading email verification service, to help ensure you are only engaging with valid contacts.

#### How It Works

When configured, RAIA Control can leverage your ZeroBounce account to validate email addresses. This process helps filter out invalid, inactive, or fake emails from your outreach lists before you send your campaigns.

#### Configuration Steps

To enable email verification, you must first connect your ZeroBounce account to RAIA Control.

1. **Obtain Your API Key:** Log in to your ZeroBounce account and navigate to the API section to find your API key.
2. **Navigate to Settings in RAIA Control:** From the main navigation sidebar, click on Settings.
3. **Add Your API Key:** Select the **Integrations** tab. You will see a dedicated field for the ZeroBounce API key. Paste your key into this field and save the configuration.

Once the API key is saved and validated, the email verification functionality will be enabled in your account.

### Enhancing Leads with the Context Field

Beyond basic contact details, true personalization comes from understanding your leads on a deeper level. RAIA Control facilitates this through the flexible Context field associated with every contact.

### The Power of the Context Field

The Context field is a JSON data object that allows you to store any additional, structured information about a contact. This is the perfect place to add enhanced data points that can be used to create highly targeted and personalized messages. This process is often referred to as lead enrichment.

For example, you could store data such as:

* Company Size
* Industry
* Specific technologies they use
* Pain points or interests identified in previous interactions

An example of a `Context` object might look like this:

```
{
"company_size": "50-100 employees",
"industry": "Software as a Service (SaaS)",
"source": "G2 Crowd",
"interests": ["AI in sales", "process automation"]
}
```

### Leveraging Enhanced Data

The data stored in the Context field is directly accessible to the AI Agents that run your missions. When you craft a mission prompt, you can instruct the agent to reference this data to tailor its communication. For instance, you could create a mission prompt that says:

> "Your goal is to book a demo. Reference the contact's industry from their context to explain how our product is relevant to their specific field."

By using the **Context** field to its full potential, you can move beyond generic templates and create conversations that are deeply relevant to each individual lead, significantly increasing your chances of engagement and success.
