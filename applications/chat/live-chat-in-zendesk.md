# Live chat in Zendesk

## Raia × Zendesk Help Center Integration Guide

A practical, copy-pasteable guide for embedding **Raia Live Chat** in a Zendesk Help Center (Guide), passing user context for tracking/analytics, and conditionally loading different chat configurations (e.g., Premium vs Standard).

***

### 0) At-a-glance

* **Where to add code in Zendesk:** `Guide Admin → Customize design → Edit code → templates/document_head.hbs` (loads on every Help Center page).
* **Minimum you need:** Raia Live Chat embed snippet (API key), a Preview or duplicate theme you can publish, and (optionally) your CSP allowlist.
* **Identity & context:** Pass `user.id`, `user.name`, and (if needed) organization names to Raia for identification and routing.
* **Conditional loading:** Load different Raia widgets (keys/config) based on user context (e.g., Premium vs Standard).

***

### Quick Start (10‑minute setup)

**Goal:** get Raia Live Chat running in your Zendesk Help Center with user context.

#### 1) Paste the embed snippet

In `templates/document_head.hbs`:

```html
<script async src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" data-api-key="YOUR_API_KEY" onload="onRaiaChatLoaded()"></script>
```

#### 2) Add the onload callback

Just above the script tag:

```html
<script>
  function onRaiaChatLoaded() {
    // Identify the signed-in user from Zendesk Curlybars
    raiaChat.sendCommand('SET_USER', {
      user: { fkId: '{{user.id}}', firstName: '{{user.name}}', email: '{{user.email}}' }
    });

    // Provide conversation context for the AI Agent
    raiaChat.sendCommand('SET_CONTEXT', { context: 'zendesk_help_center' });

    // Optional: let the agent use current page text as context
    // raiaChat.sendCommand('ENABLE_CURRENT_PAGE_TEXT');
  }
</script>
```

#### 3) Publish & test

* Preview the theme → open an article page → verify the launcher appears.
* Start a chat; confirm your user appears in Raia with the correct `fkId` and email.

**That’s it.** You can now fine‑tune behavior with the SDK commands below and (optionally) set up Premium vs Standard keys and asynchronous Zendesk escalation.

***

### 1) Embed the Raia Live Chat agent

Paste your Raia snippet near the bottom of **`document_head.hbs`**, just before `</head>`.

```html
<!-- Raia Live Chat -->
<script async src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" data-api-key="YOUR_API_KEY" onload="window.onRaiaChatLoaded && window.onRaiaChatLoaded()"></script>
```

**Tips**

* Use a **Preview** or a **cloned theme** first. After verification, click **Publish**.
* For multi-brand: repeat in each brand’s active theme (or only where you want Raia).

***

### 2) Pass user context from Zendesk to Raia (via Live Chat SDK)

Use the **Live Chat SDK** to pass identity and context after the script loads. Choose one approach.

#### Option A — Onload + SDK (simple & recommended)

```html
<script>
  function onRaiaChatLoaded() {
    // Identify the signed-in user from Zendesk Curlybars
    raiaChat.sendCommand('SET_USER', {
      user: {
        fkId: '{{user.id}}',
        firstName: '{{user.name}}',
        email: '{{user.email}}'
      }
    });

    // Provide conversation context for the AI Agent
    raiaChat.sendCommand('SET_CONTEXT', { context: 'zendesk_help_center' });

    // (Optional) Allow the agent to use current page text as context
    // raiaChat.sendCommand('ENABLE_CURRENT_PAGE_TEXT');
  }
</script>
<script async src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" data-api-key="YOUR_API_KEY" onload="onRaiaChatLoaded()"></script>
```

#### Option B — Global object + SDK (richer payloads)

```html
<script>
  window.RAIA_CONTEXT = {
    user: {
      fkId: '{{user.id}}',
      firstName: '{{user.name}}',
      email: '{{user.email}}',
      organizations: [ {{#each user.organizations}}"{{name}}"{{#unless @last}},{{/unless}}{{/each}} ]
    },
    page: { url: location.href, title: document.title }
  };
  function onRaiaChatLoaded() {
    raiaChat.sendCommand('SET_USER', { user: window.RAIA_CONTEXT.user });
    raiaChat.sendCommand('SET_CONTEXT', { context: 'help_center' });
  }
</script>
<script async src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" data-api-key="YOUR_API_KEY" onload="onRaiaChatLoaded()"></script>
```

#### Option C — JSON script tag + SDK (safe escaping)

```html
<script id="raia-user" type="application/json">{ "fkId": "{{user.id}}", "firstName": "{{user.name}}", "email": "{{user.email}}" }</script>
<script>
  function onRaiaChatLoaded() {
    try {
      const raw = document.getElementById('raia-user')?.textContent || '{}';
      raiaChat.sendCommand('SET_USER', { user: JSON.parse(raw) });
      raiaChat.sendCommand('SET_CONTEXT', { context: 'help_center' });
    } catch(e) {}
  }
</script>
<script async src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" data-api-key="YOUR_API_KEY" onload="onRaiaChatLoaded()"></script>
```

***

### 3) Identify the user in Raia for tracking & routing (SDK)

Use the SDK commands in your `onRaiaChatLoaded` callback:

```html
<script>
  function onRaiaChatLoaded() {
    const u = window.RAIA_CONTEXT?.user || { fkId: '{{user.id}}', firstName: '{{user.name}}', email: '{{user.email}}' };

    // Identify the user for tracking/memory
    raiaChat.sendCommand('SET_USER', { user: u });

    // Attach conversation/session context for the AI Agent
    raiaChat.sendCommand('SET_CONTEXT', {
      context: 'zendesk_help_center/{{help_center.name}}/{{help_center.locale}}'
    });
  }
</script>
```

This enables attribution, routing (e.g., Premium), and cleaner analytics.

***

### 4) Conditional loading (e.g., Premium vs Standard)

Load the correct key/config at runtime based on user attributes.

```html
<script>
  const orgsCSV = '{{#each user.organizations}}{{name}}{{#unless @last}},{{/unless}}{{/each}}';
  const isPremium = (orgsCSV || '').split(',').map(s=>s.trim()).includes('Premium');
  const apiKey = isPremium ? 'YOUR_PREMIUM_API_KEY' : 'YOUR_STANDARD_API_KEY';

  function onRaiaChatLoaded() {
    raiaChat.sendCommand('SET_USER', { user: { fkId: '{{user.id}}', firstName: '{{user.name}}' } });
    raiaChat.sendCommand('SET_CONTEXT', { context: isPremium ? 'premium' : 'standard' });
  }

  const s = document.createElement('script');
  s.src = 'https://raiabot.raia2.com/assets/raia-chatbot-widget.js';
  s.async = true;
  s.setAttribute('data-api-key', apiKey);
  s.onload = onRaiaChatLoaded;
  document.head.appendChild(s);
</script>
```

***

### 5) Content Security Policy (CSP)

If your Help Center enforces CSP, add Raia endpoints. Example (tighten as needed):

```
script-src   https://raiabot.raia2.com;
connect-src  https://api.raia2.com https://raiabot.raia2.com YOUR_BACKEND_HOST;
img-src      https://raiabot.raia2.com data:;
frame-src    https://raiabot.raia2.com;
```

***

### 6) Escalation to Zendesk (Recommended: **Asynchronous Ticket Handoff**)

Standard approach for clients: **Raia Live Chat collects transcript & context and a Zendesk Support ticket is created via API**. An agent follows up by email. If a synchronous human conversation is needed, your team can initiate a **live transfer via Raia Co‑Pilot**.

#### 6.1 What clients configure

* **When to escalate:** keywords ("human"), low-confidence paths, premium users, or specific flows.
* **What to send:** requester identity (email/name or external id), summary subject, transcript (or link), plan/brand/locale/org, and any relevant tags.
* **Where to send:** your backend endpoint that calls the Zendesk **Tickets API** (keep credentials server-side).
* **What users see:** a confirmation message in the Raia widget (with optional ticket number) and an email reply from Support.

#### 6.2 UI copy (ready to paste)

> “I’ve shared this conversation with our support team. You’ll get an email update shortly. Ticket: **#\{{ticket\_id\}}**.”

#### 6.3 Best practices

* Use a **stable external ID** to join Raia sessions to Zendesk users.
* Route Premium customers via group/priority/tags.
* Keep PII minimal; enrich server-side.
* Verify requests from Raia to your backend (shared secret/JWT).

***

### 7) Developer access

* **Zendesk:** API token/OAuth, custom fields, groups.
* **Infra:** A minimal endpoint (Cloud Run/Functions) that calls Zendesk Tickets API.
* **Raia:** Configure escalation rules; access to conversation IDs/transcripts.

***

### 8) Live Chat SDK Reference

#### Commands

* `OPEN_CHAT` `{ page }`
* `CLOSE_CHAT`
* `SEND_MESSAGE` `{ message }`
* `SET_USER` `{ user: { fkId, fkUserId?, firstName?, lastName?, email?, phoneNumber?, customData? } }`
* `CLEAR_USER`
* `SET_CONTEXT` `{ context }`
* `CLEAR_CONTEXT`
* `ENABLE_CURRENT_PAGE_TEXT`
* `DISABLE_CURRENT_PAGE_TEXT`

#### Usage notes

* Always call `raiaChat.sendCommand(...)` **after** the script loads.
* Use the script tag’s `onload` attribute or a window callback (`onRaiaChatLoaded`).

#### Example onload usage

```html
<script>
  function onRaiaChatLoaded() {
    raiaChat.sendCommand("OPEN_CHAT", { page: "chat" });
    raiaChat.sendCommand("SET_CONTEXT", { context: "test context" });
    raiaChat.sendCommand("ENABLE_CURRENT_PAGE_TEXT");
    raiaChat.sendCommand("SET_USER", {
      user: {
        email: "test@test.com",
        fkId: "123",
        fkUserId: "456",
        customData: { productId: "dk3j02k", quantity: 10 }
      }
    });
  }
</script>

<script async src="https://raiabot.raia2.com/assets/raia-chatbot-widget.js" data-api-key="YOUR_API_KEY" onload="onRaiaChatLoaded()"></script>
```

#### Example integration

* [CodeSandbox demo](https://codesandbox.io/p/sandbox/4w5g86)

***

### 9) Full Implementation Plan

#### Phase 1 — Enable the widget

1. Add embed snippet + `onRaiaChatLoaded` (Quick Start above).
2. Verify widget loads on homepage, category, article, and search pages.

#### Phase 2 — Identify users & context

1. Pass `SET_USER` (at minimum `fkId`, optionally name/email).
2. Pass `SET_CONTEXT` with a simple source tag (`zendesk_help_center`).
3. (Optional) `ENABLE_CURRENT_PAGE_TEXT` for richer context.

#### Phase 3 — Conditional experiences

1. Decide how to determine Premium vs Standard (org name, SSO claim, etc.).
2. Use conditional loader to choose the correct `data-api-key`.

#### Phase 4 — Escalation to Zendesk (asynchronous)

1. Configure escalation rules in your Raia agent (keywords/low confidence/premium).
2. On escalate, your backend creates a Zendesk ticket via API with transcript/context.
3. Confirm widget copy shows ticket ID and email follow‑up expectations.

#### Phase 5 — Compliance & CSP

1. Add CSP allowlist for `https://raiabot.raia2.com` and `https://api.raia2.com` (see §5).
2. Minimize PII; prefer stable IDs.

#### Phase 6 — QA & Launch

1. Test signed‑in vs anonymous users.
2. Test Premium vs Standard routing.
3. Test escalation path end‑to‑end (ticket created, email received).
4. Publish in a low‑traffic window; monitor for 24–48h.

***

### 10) Rollout Plan (Checklist)

1. **Clone** current theme → create **Staging** theme.
2. Add SDK embed + context passing (and conditional logic if needed).
3. **Preview** across key page types; validate identity & CSP.
4. Configure **asynchronous escalation** endpoint; test with Premium/Standard.
5. **Publish** during a low-traffic window.
6. **Monitor** logs and Zendesk ticket creation for 48h; have rollback ready.

