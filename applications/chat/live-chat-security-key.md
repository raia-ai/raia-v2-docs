---
description: >-
  Generate a Security Key in Live Chat settings to restrict access. Once
  enabled, the widget won’t load unless you pass the key during initialization.
---

# Live Chat Security Key

This article will walk you through generating a key and implementing the necessary code.

### Step 1: Generate a Security Key

**First, you need to generate the key from your admin panel.**

1. Navigate to **Live Chat > Security.**
2. In the Security **Key and Origins section**, click **Generate Security Key**.
3. **Copy** the generated key immediately. You will need it for your code.
4. Click **Save** to activate the key.

Once saved, your live chat widget will be blocked on your website until you complete the next step.

### Step 2: Implement the Security Key in Your Code

To unblock the chat, you must pass the security key when the widget loads. This is done by using the `onload` attribute on your script tag to call a function that sends the `INIT` command.

### The Code Logic

1. The standard chat widget script is loaded with the `async` attribute.
2. The `data-api-key` attribute still contains your **Agent ID**.
3. The `onload="onRaiaChatLoaded()"` attribute is added to the script tag. This tells the browser to execute the `onRaiaChatLoaded` function as soon as the script is finished loading.
4. Inside the `onRaiaChatLoaded` function, you use the SDK command `raiaChat.sendCommand()`.
5. You send the `INIT` command and pass an object containing the `apiKey` field.

> I**mportant Note:** The `apiKey` field inside the `INIT` command must contain your **Security Key**, not your Agent ID. This is a special use case specifically for security key initialization.

### Code Implementation

Here is the complete code you need to add to your website. Replace the placeholder values with your actual Agent ID and Security Key.

```
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Live Chat with Security Key</title>

    <script>
      // This function is called automatically when the chat widget script has loaded
      async function onRaiaChatLoaded() {
        // Send the INIT command with the Security Key
        window.raiaChat.sendCommand("INIT", {
          apiKey: "YOUR_SECURITY_KEY_HERE", // Paste the key you generated here
        });
      }
    </script>
  </head>

  <body>
    <h1>Your Page Content</h1>

    <!-- The Raia Chatbot Widget Script -->
    <script
      async
      src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js"
      data-api-key="YOUR_AGENT_ID_HERE"
      onload="onRaiaChatLoaded( )"
    ></script>
  </body>
</html>

```

### Summary of Placeholders

| Placeholder              | Your Value                                         |
| ------------------------ | -------------------------------------------------- |
| `YOUR_SECURITY_KEY_HERE` | The Security Key you generated in the admin panel. |
| `YOUR_AGENT_ID_HERE`     | The Agent ID from your Live Chat settings.         |

Once you have implemented this code, your Live Chat widget will load securely on your website. If the security key is incorrect or missing, the chat will remain blocked.
