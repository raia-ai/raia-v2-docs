# API Documentation

The API Documentation can be [found here](https://api.raia2.com/api/external/docs).

{% hint style="info" %}
For **OpenAPI** specifications you can [view here](https://api.raia2.com/api/external/docs/openapi.json). OpenAPI is a widely used, industry-standard format for describing HTTP APIs. It was previously known as Swagger and is now maintained by the OpenAPI Initiative. OpenAPI documents provide a machine-readable and human-friendly way to define and understand REST APIs, enabling developers to design, build, and consume APIs more effectively.&#x20;
{% endhint %}

Each Agent has an API Key which you generated under the API Skill when editing the Agent,

Pass the API Key via the header as **Agent-Secret-Key**

**Example: Conversations Start**

```
curl -X POST https://api.raia2.com/external/conversations/start \
  -H "Content-Type: application/json" \
  -H "Agent-Secret-Key: XXXXXXXXXX" \
  -d '{
    "firstName": "Greg",
    "lastName": "Giglio",
    "channel": "sms",
    "context": "You are talking with mortgage lead Greg Giglio. Their email is XXXXXXXX Their phone is XXXXXXX. They previously spoke with Andrew S. Russell at RCG Mortgage. You are reconnecting with this opportunity to see if they are in the market for a mortgage.",
    "source": "CRM",
    "fkId": "12345",
    "fkUserId": "123456789", 
    "email": "demo@demo.com",
    "phoneNumber": "+14567890101", 
    "smsIntroduction": "Hi, Greg. It's Mindy"
  }'

```

