---
description: >-
  raia's Live Chat SDK lets you customize the chat experience. You can pass user
  info and context, send messages programmatically, and fully control the chat
  interface.
---

# Live Chat SDK

This article covers the two primary integration methods: the **Embed JS SDK** and the **Iframe SDK.**&#x20;



## Key Capabilities

* Set user information for tracking and conversation memory.&#x20;
* Set message-level and conversation-level context to improve responses.&#x20;
* Override the welcome message shown in the chat UI.&#x20;
* Open/close the chat, send messages programmatically, and reset the conversation.&#x20;
* Enable/disable using the current page text as context.



## Choosing Your Integration Method

* There are two ways to integrate the Live Chat, each suited for different needs:&#x20;

1. **Embed JS SDK (Recommended):** This is the simplest and most common method. A single script tag automatically injects a floating chat widget with a launcher button onto your page. It's quick to set up and handles most of the UI for you.&#x20;
2. **Iframe SDK:** This method is for advanced use cases where you need full control over the chat container. You embed the chat inside an \<iframe> that you manage, allowing it to be placed anywhere in your page layout.&#x20;

Both methods support a similar set of commands for interacting with the chat.&#x20;



### Embed JS SDK (recommended)

This method is recommended for most users. It adds a floating chat widget to your site with minimal configuration.&#x20;

### 1. Basic Setup&#x20;

To get started, add the following script tag to your HTML. The widget will automatically load and appear on your site.&#x20;

```
<script 
  async 
  src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" 
  data-api-key="YOUR_AGENT_ID"> 
</script> 
```

**data-api-key** must be your **Agent ID** from the Launch tab in Raia. Do not use an API/Security Key here.



### 2. Working Example&#x20;

The following example demonstrates how to use the Embed JS SDK to interact with the chat widget. This code shows how to set context, define user information, and send messages programmatically.&#x20;

**Important:** To use `raiaChat.sendCommand`, make sure the script is loaded before calling it. Example:

```
<!DOCTYPE html> 
<html lang="en"> 
<head> 
  <meta charset="UTF-8" /> 
  <meta name="viewport" content="width=device-width, initial-scale=1.0" /> 
  <title>Embed JS SDK Example</title> 
 
  <script> 
    // Called once the chat widget is fully loaded 
    async function onRaiaChatLoaded() { 
      const raiaChat = window.raiaChat; 
 
      raiaChat.sendCommand("SET_WELCOME_MESSAGE", { 
        message: "Welcome! How can I help you today?", 
      }); 
 
      raiaChat.sendCommand("SET_USER", { 
        user: { 
          firstName: "Jane", 
          email: "jane.doe@example.com", 
          fkId: "customer-12345", 
          customData: { 
            plan: "Premium", 
            isLoggedIn: true, 
          }, 
        }, 
      }); 
    } 
 
    function sendCustomMessage() { 
      const raiaChat = window.raiaChat; 
 
      raiaChat.sendCommand("SET_CONTEXT", { 
        context: "User is on the pricing page.", 
      }); 
 
      raiaChat.sendCommand("SEND_MESSAGE", { 
        message: "I have a question about the enterprise plan.", 
      }); 
 
      raiaChat.sendCommand("OPEN_CHAT", { page: "chat" }); 
    } 
  </script> 
 
  <script 
    async 
    src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" 
    data-api-key="YOUR_AGENT_ID" 
    onload="onRaiaChatLoaded()" 
  ></script> 
</head> 
<body> 
  <h1>Embed JS SDK Demonstration</h1> 
  <button onclick="sendCustomMessage()">Ask a Question</button> 
</body> 
</html> 
```

### 3. SDK Command Reference

Once the widget script is loaded, you can control it using `raiaChat.sendCommand()` Because the script loads asynchronously, wait until the SDK is ready before calling commands.

```
function whenRaiaChatReady(callback) { 
  if (window.raiaChat && typeof window.raiaChat.sendCommand === "function") { 
    callback(window.raiaChat); 
  } else { 
    setTimeout(() => whenRaiaChatReady(callback), 200); 
  } 
} 
 
whenRaiaChatReady((raiaChat) => { 
  raiaChat.sendCommand("OPEN_CHAT", { page: "chat" }); 
}); 
```



**Available commands:**

<table><thead><tr><th>Command</th><th>Description</th><th width="232">Payload (example)</th></tr></thead><tbody><tr><td><code>INIT</code></td><td>Initializes the chat session (API key only if required in your environment).</td><td><p><code>{ apiKey?:</code> </p><p><code>"YOUR_API_KEY" }</code></p></td></tr><tr><td><code>OPEN_CHAT</code></td><td>Opens the chat window.</td><td><code>{ page?: 'home'| 'chat' }</code></td></tr><tr><td><code>CLOSE_CHAT</code></td><td>Closes the chat window.</td><td>-</td></tr><tr><td><code>SEND_MESSAGE</code></td><td>Sends a message as the user.</td><td><code>{ message: string }</code></td></tr><tr><td><code>SET_USER</code></td><td>Sets the user’s information.</td><td><code>{ user: { fkId?, fkUserId?, firstName?, lastName?, email?, phoneNumber?, customData? } }</code></td></tr><tr><td><code>CLEAR_USER</code></td><td>Clears the user's information.</td><td>-</td></tr><tr><td><code>SET_CONTEXT</code></td><td>Sets context used for the next interaction/message.</td><td><code>{ context: string }</code></td></tr><tr><td><code>CLEAR_CONTEXT</code></td><td>Clears message-level context.</td><td>-</td></tr><tr><td><code>SET_CONVERSATION_CONTEXT</code></td><td>Sets context for the entire conversation.</td><td><code>{ context: string }</code></td></tr><tr><td><code>SET_WELCOME_MESSAGE</code></td><td>Overrides the default welcome message.</td><td><code>{ message: string }</code></td></tr><tr><td><code>ENABLE_CURRENT_PAGE_TEXT</code></td><td>Allows the AI to use the current page text as context.</td><td>-</td></tr><tr><td><code>DISABLE_CURRENT_PAGE_TEXT</code></td><td>Prevents the AI from using the current page text as context.</td><td>-</td></tr><tr><td><code>RELOAD</code></td><td>Reloads the chat application.</td><td>-</td></tr><tr><td><code>REFETCH_CONFIG</code></td><td>Forces the chat to pull the latest configuration from the server.</td><td>-</td></tr><tr><td><code>DELETE_CHAT</code></td><td>Wipes the current conversation.</td><td>-</td></tr></tbody></table>

### 4. Customizing the Chat Widget Appearance (CSS)

You can override the default widget styles with your own CSS. The widget injects its base styles into the host page at runtime (via an inline `<style>` tag). Make sure your custom stylesheet is loaded **after** the widget script or use `!important` to ensure your styles are applied (sparingly).

#### 4.1 Quick customization (common classes)

**Targetable CSS Classes:**

* **`.raia-chat-container`** – The main chat widget container that holds the iframe with the chat UI. This is the element that’s fixed in the bottom-right corner and controls size, position, border-radius, box-shadow, etc.
* **`.raia-chat-container-open`** – Applied to the same container when the chat is opened. Controls visibility, opacity, pointer-events, and the open/closed transition. Toggling this class is what shows/hides the widget.
* **`.raia-chat-button`** – The floating launcher button container (the round button you click to open the chat). Controls fixed positioning, cursor, border-radius, margins, and the hover transform.
* **`.raia-chat-button-icon`** – The `<img>` inside the launcher button (the avatar/icon). Controls its size and circular shape.

These class names are defined as constants in `src/chatbotWidget/constants.ts` and then used both for DOM creation and for the default injected styles, so overriding them in your own stylesheet (loaded after the widget script) is the supported way to customize positioning and appearance from the host page.

**Example: reposition and restyle the widget**

```css
/* Reposition the chat window to the bottom-left */ 
.raia-chat-container { 
  right: auto !important; 
  left: 32px !important; 
  bottom: 96px !important; 
} 
 
/* Restyle the launcher button */ 
.raia-chat-button { 
  right: auto !important; 
  left: 32px !important; 
  bottom: 24px !important; 
  background: linear-gradient(135deg, #2563eb, #4f46e5) !important; 
} 
```

**Example: use a custom launcher button**

A common use case is to hide the default button and open the chat from another element, like a button in your navigation bar.

Hide the default button and open the chat from your own UI element:

```
/* Hide the default floating launcher button */ 
.raia-chat-button { 
  display: none !important; 
} 

```

```
<button id="my-custom-chat-button">Chat with Support</button> 
 
<script> 
  function whenRaiaChatReady(callback) { 
    if (window.raiaChat && typeof window.raiaChat.sendCommand === "function") { 
      callback(window.raiaChat); 
    } else { 
      setTimeout(() => whenRaiaChatReady(callback), 200); 
    } 
  } 
 
  document.getElementById("my-custom-chat-button").addEventListener("click", () => { 
    whenRaiaChatReady((raiaChat) => { 
      raiaChat.sendCommand("OPEN_CHAT", { page: "chat" }); 
    }); 
  }); 
</script> 

```

#### 4.2 Advanced: Overriding base styles (BEM classes)

The Raia chatbot widget injects its base styles into the host page at runtime (via an inline `<style>` tag). When embedding on an external site, you can override these base styles by adding your own CSS rules that target the widget’s public class names.

**How overrides work**

* The widget’s base CSS is injected at runtime.
* Your site CSS can override it using:
  * More specific selectors, or
  * `!important` (use sparingly)

**Public CSS classes (BEM)**

The widget uses the `raia-chat-widget__*` namespace for elements.

**Block**

* `.raia-chat-widget`

**Elements**

* `.raia-chat-widget__container` — floating chat container (contains the `<iframe>`)
* `.raia-chat-widget__launcher` — fixed-position launcher container
* `.raia-chat-widget__button` — clickable launcher button
* `.raia-chat-widget__button-image` — `<img>` inside the button (avatar mode)
* `.raia-chat-widget__button-text` — `<p>` inside the button (text-only mode)
* `.raia-chat-widget__tooltip` — tooltip shown for icon+text mode
* `.raia-chat-widget__suggestions` — suggestions popup container
* `.raia-chat-widget__suggestion` — a single suggestion button

**Modifiers / state**

* `.raia-chat-widget__container--open` — applied when chat is open
* `.raia-chat-widget__tooltip--visible` — applied when tooltip is visible
* `.raia-chat-widget__suggestions--visible` — applied when suggestions popup is visible
* `.raia-chat-widget__launcher--icon-and-text` — applied when tooltip is shown (icon+text mode)

**View mode and size (public)**

These classes can be used for conditional overrides:

* `.raia-chat-mode-popup` / `.raia-chat-mode-sidebar`
* `.raia-chat-size-small` / `.raia-chat-size-medium` / `.raia-chat-size-big` / `.raia-chat-size-full_height`



**Recommended override pattern**

Create a small CSS file in your host site and load it after any CSS reset and your base theme. If you want to avoid affecting other widgets or pages, scope your overrides to a page wrapper (example: `body.customer-portal`).

```
/* 1) Scope overrides (recommended) */
body.customer-portal .raia-chat-widget__launcher {
  right: 24px;
  bottom: 24px;
}

/* 2) Customize container (chat window) */
body.customer-portal .raia-chat-widget__container {
  width: 420px;
  border-radius: 18px;
}

/* 3) Example: different width for sidebar mode */
body.customer-portal .raia-chat-widget__container.raia-chat-mode-sidebar {
  width: 520px;
}

/* 4) Customize launcher button */
body.customer-portal .raia-chat-widget__button {
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.18);
}

/* 5) Tooltip styling */
body.customer-portal .raia-chat-widget__tooltip {
  font-family: inherit;
  border-radius: 10px;
}

/* 6) Suggestions */
body.customer-portal .raia-chat-widget__suggestions {
  gap: 10px;
}
body.customer-portal .raia-chat-widget__suggestion {
  border-radius: 10px;
}

```

**When to use `!important`**

Prefer selector specificity first. If you must force an override (e.g., your CSS loads before the widget script and you cannot change order), use `!important` on a small number of properties.

**Safe properties to override**

Safe:

* Layout/position: `right`, `bottom`, `width`, `height`, `max-height`
* Visual: `border-radius`, `box-shadow`, `background`, `font-family`, `font-size`

Be careful with:

* `pointer-events` and `visibility` (used for open/close behavior)
* `transform` and `opacity` (used for animations/transitions)

**Troubleshooting**

If your styles don’t apply:

* Confirm your selector matches the element class
* Increase specificity (add a page scope / parent selector)
* As a last resort, use `!important`

If the widget becomes unclickable:

* Check you didn’t override `pointer-events` on launcher/button elements

## Iframe SDK

Use the Iframe SDK for advanced cases where you need full control over the chat container placement. You embed the chat inside an that you manage.

### 1. Iframe setup&#x20;

Add an `<iframe>` to your HTML. Then, include the `raia-chatbot-iframe.js`  script and instantiate the `raiaiframechat` class.

```
<div class="raia-chat-wrapper"> 
  <iframe 
    id="raia-chat-iframe" 
    class="raia-chat-iframe" 
    src="https://raiabot.raia2.com/YOUR_AGENT_ID/chat" 
    allow="camera; microphone;" 
  ></iframe> 
</div> 
 
<script src="https://raiabot.raia2.com/assets/raia-chatbot-iframe.js"></script> 
 
<script> 
  const raiaIframeChat = new window.RaiaIframeChat({ 
    iframeId: "raia-chat-iframe", 
    isSecurityKeyRequired: true, // set to false if you don’t use an API key 
  }); 
 
  window.addEventListener("DOMContentLoaded", () => { 
    raiaIframeChat.sendCommand("INIT", { 
      apiKey: "YOUR_API_KEY", 
    }); 
  }); 
</script> 
```



### 2. SDK Command Reference (Iframe)&#x20;

The commands for the Iframe SDK are identical to the Embed JS SDK. You use them via the `raiaiframechat` instance you created.

```
raiaIframeChat.sendCommand("OPEN_CHAT", { page: "chat" }); 
raiaIframeChat.sendCommand("SEND_MESSAGE", { message: "Hello!" }); 
```

### 3. CSS Customization (Iframe)&#x20;

With the Iframe SDK, you have full control over the `<iframe>` and its container. The internal chat UI is styled via your Live Chat Design settings.&#x20;

```
/* Outer wrapper for the iframe */ 
.raia-chat-wrapper { 
  position: relative; /* or absolute/fixed */ 
  width: 420px; 
  height: 600px; 
  max-height: 80vh; 
  border-radius: 24px; 
  overflow: hidden; 
  box-shadow: 0 18px 45px rgba(15, 23, 42, 0.45); 
} 
 
/* The iframe itself */ 
.raia-chat-iframe { 
  display: block; 
  width: 100%; 
  height: 100%; 
  border: none; 
} 
```
