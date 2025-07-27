# Table of contents

## Introduction

* [Welcome to raia](README.md)
  * [Why use raia](introduction/welcome-to-raia/why-use-raia.md)
  * [Core Features of raia](introduction/welcome-to-raia/core-features-of-raia.md)

***

* [Launching an AI Agent](launching-an-ai-agent/README.md)
  * [Quick Step-by-Step Guide](launching-an-ai-agent/quick-step-by-step-guide.md)
  * [Multi-Agent Architecture](launching-an-ai-agent/multi-agent-architecture.md)
* [AI Training](ai-training/README.md)
  * [Setup of Instructions](ai-training/setup-of-instructions.md)
  * [Documents for Training](ai-training/documents-for-training.md)
  * [Setup of Knowledge Base](ai-training/setup-of-knowledge-base.md)
* [AI Agent Skills](ai-agent-skills/README.md)
  * [Live Chat Skill](ai-agent-skills/live-chat-skill.md)
  * [SMS Skill](ai-agent-skills/sms-skill.md)
  * [Email Skill](ai-agent-skills/email-skill.md)
  * [Voice Skill](ai-agent-skills/voice-skill.md)
  * [Scoring Skill](ai-agent-skills/scoring-skill.md)
  * [Webhooks Skill](ai-agent-skills/webhooks-skill.md)
  * [API Skill](ai-agent-skills/api-skill.md)
  * [Functions Skill](ai-agent-skills/functions-skill.md)
  * [Memory Skill](ai-agent-skills/memory-skill.md)
  * [Notifications Skill](ai-agent-skills/notifications-skill.md)
  * [Reporting Skill](ai-agent-skills/reporting-skill.md)
  * [Retrieval Skill](ai-agent-skills/retrieval-skill.md)
  * [Scraping Skill](ai-agent-skills/scraping-skill.md)
  * [Web Search Skill](ai-agent-skills/web-search-skill.md)
* [AI Agent Packs](ai-agent-packs.md)
* [AI Security](ai-security/README.md)
  * [Setup of Access Control](ai-security/setup-of-access-control.md)
  * [Monitoring & Reporting](ai-security/monitoring-and-reporting.md)
* [Integration](integration/README.md)
  * [API Documentation](integration/api-documentation.md)
  * [n8n Node](integration/n8n-node.md)

## PRODUCT TOUR + FEATURES

* [Setting up Account](product-tour-+-features/setting-up-account.md)

***

* [Building an AI Agent](building-an-ai-agent.md)
* [Agent Skill Tab](agent-skill-tab.md)
* [Agent API Integration Skill](agent-api-integration-skill.md)
* [Agent Email Skill](agent-email-skill.md)
* [Agent Live Chat](agent-live-chat.md)
* [Agent Memory Skill](agent-memory-skill.md)
* [Agent Notification Skill](agent-notification-skill.md)
* [Agent Web Search Skill](agent-web-search-skill.md)
* [Agent Report Skill](agent-report-skill.md)
* [Agent Scoring Skill](agent-scoring-skill.md)
* [Agent SMS Skill](agent-sms-skill.md)
* [Agent Scraper Skill](agent-scraper-skill.md)
* [Agent Voice Skill](agent-voice-skill.md)
* [Agent External Retriever Skill](agent-external-retriever-skill.md)
* [Agent Webhook Skill](agent-webhook-skill.md)
* [Agent Function Skill](agent-function-skill.md)
* [Launchpad Agents Tab](launchpad-agents-tab.md)
* [Agent Training Tab](agent-training-tab.md)
* [Agent Security Tab](agent-security-tab.md)
* [Launch Agent Tab](launch-agent-tab.md)
* [Agent Report Tab](agent-report-tab.md)
* [Agent Info Tab](agent-info-tab.md)
* [LaunchPad Packs](launchpad-packs.md)
* [Launchpad Functions](launchpad-functions.md)
* [Launchpad Users Tab](launchpad-users-tab.md)
* [LaunchPad Users (Basic Information)](launchpad-users-basic-information.md)
* [Launchpad Conversations Tab](launchpad-conversations-tab.md)
* [Launchpad Resource Usage Tab](launchpad-resource-usage-tab.md)
* [Launchpad Logs Tab](launchpad-logs-tab.md)
* [Debug](debug.md)
* [Launchpad Settings](launchpad-settings.md)
* [Copilot Menu](copilot-menu.md)
* [Copilot Admin Mode](copilot-admin-mode.md)
* [Copilot Conversation Tab](copilot-conversation-tab.md)

## Applications

* [Copilot](applications/copilot/README.md)
  * [Copilot vs Chat GPT](applications/copilot/copilot-vs-chat-gpt.md)
  * [How it works](applications/copilot/how-it-works.md)
  * [Admin Mode](applications/copilot/admin-mode.md)
  * [Human in the Loop](applications/copilot/human-in-the-loop.md)
  * [Human Feedback](applications/copilot/human-feedback.md)
* [Live Chat](applications/live-chat/README.md)
  * [Live Chat SDK](applications/live-chat/live-chat-sdk.md)
* [Academy](applications/academy.md)

## Launch Plan

* [Checklist](launch-plan/checklist.md)
* [raia Setup](launch-plan/raia-setup.md)
* [AI Agent Roles](launch-plan/ai-agent-roles/README.md)
  * [AI Sales Agent](launch-plan/ai-agent-roles/ai-sales-agent.md)
  * [AI Support Agent](launch-plan/ai-agent-roles/ai-support-agent.md)
  * [AI Content Writer](launch-plan/ai-agent-roles/ai-content-writer.md)
  * [AI Project Manager](launch-plan/ai-agent-roles/ai-project-manager.md)
* [Training](launch-plan/training.md)
* [Integration](launch-plan/integration.md)
* [Testing](launch-plan/testing/README.md)
  * [Reasons for Bad Responses](launch-plan/testing/reasons-for-bad-responses.md)

## OpenAI

* [OpenAI Integration](openai/openai-integration.md)

## raia API Specifications

* ```yaml
  type: builtin:openapi
  props:
    models: true
  dependencies:
    spec:
      ref:
        kind: openapi
        spec: raia-ai-api
  ```
