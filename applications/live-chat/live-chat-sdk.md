---
description: >-
  The following is SDK Documentation on how to customize the Live Chat
  experience.
---

# Live Chat SDK

## Live Chat Customization

To pass variables to the Live Chat can be done using our SDK. This is important if you want to pass information to the AI Agent (via Live Chat) much like you pass via our API.&#x20;

You can do the following:

1. Set User - This will add the user into raia for tracking / memory
2. Set Context - This provide context of the conversation for the AI Agent. \


Command usage:

```
// 1. Open the chat
raiaChat.sendCommand('OPEN_CHAT', { page: 'chat' });

// 2. Close the chat
raiaChat.sendCommand('CLOSE_CHAT');

// 3. Send a message
raiaChat.sendCommand('SEND_MESSAGE', { message: 'Hello! I need some help.' });

// 4. Set user info
raiaChat.sendCommand('SET_USER', {
  user: {
    fkId: 'abc123',
    fkUserId: 'user456',
    firstName: 'Jane',
    lastName: 'Doe',
    email: 'jane@example.com',
    phoneNumber: '+1234567890',
  },
});

// 5. Clear user
raiaChat.sendCommand('CLEAR_USER');

// 6. Set context
raiaChat.sendCommand('SET_CONTEXT', { context: 'checkout_support' });

// 7. Clear context
raiaChat.sendCommand('CLEAR_CONTEXT');
```

Important: To use `raiaChat.sendCommand`, make sure the script is loaded before calling it. Example:

```
<script>
  function onRaiaChatLoaded() {
    raiaChat.sendCommand("OPEN_CHAT", { page: "chat" });
    raiaChat.sendCommand("SET_CONTEXT", { context: "test context" });
    raiaChat.sendCommand("ENABLE_CURRENT_PAGE_TEXT");
    raiaChat.sendCommand("SET_USER", {
      user: { 
        email: "test@test.com" 
        fkId: “123”,
        fkUserId: “456",
        customData: {
        productId: “dk3j02k”,
        quantity: 10
    }},
    });

  }
</script>

<script
  async
  src=""
  data-api-key="5ac087fb-06d2-4219-8bae-b393c8db549f"
  onload="onRaiaChatLoaded()"
></script>
```

Example integration can be found here [https://codesandbox.io/p/sandbox/4w5g86](https://codesandbox.io/p/sandbox/4w5g86)

```
New Commands Available for SDK

-- To add content from webpage the Live Chat is on -

Use:

    raiaChat.sendCommand("ENABLE_CURRENT_PAGE_TEXT");
    raiaChat.sendCommand("DISABLE_CURRENT_PAGE_TEXT");
```
