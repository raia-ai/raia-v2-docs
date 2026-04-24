# MCP with Windsurf

## MCP Server Configuration Guide

This guide provides step-by-step instructions for configuring the Model Context Protocol (MCP) server to connect with your Raia agent through IDEs like Windsurf or Cursor.

**Windsurf Docs:** [https://docs.windsurf.com/windsurf/cascade/mcp#adding-a-new-mcp](https://docs.windsurf.com/windsurf/cascade/mcp#adding-a-new-mcp)

### Configuration Steps

#### 1. Configure MCP Skill for Agent

* Navigate to agent skills in Raia UI
* Select MCP skill and click "Set up MCP Skill"
* Generate unique API key (UUID) for your agent

#### 2. Get API Key and Server URL

* Copy the generated API key from MCP skill page
* Use server URL: `https://api-dev.raia2.com/mcp`

#### 3. Configure MCP Connection in IDE

* **Windsurf**: Add server configuration with name, serverUrl, and Authorization header
* **Cursor**: Configure mcp.servers with URL and Authorization header
* **Generic**: Use YAML format with name, url, and Authorization header

**Example configuration:**

```json
"raia": {
  "disabled": false,
  "headers": {
    "Authorization": "uuid-dsfsdfsdfasdfasdfasdfasdf"
  },
  "serverUrl": "https://api.raia2.com/mcp"
}
```

#### 4. How IDE Knows When to Call MCP

The IDE automatically detects and calls your MCP server when:

* **User asks questions**: When you type questions or prompts in the IDE's chat/interface
* **Tool invocation needed**: When the AI determines it needs external tools or capabilities
* **Context requires agent interaction**: When the conversation requires your specific agent's knowledge or skills
* **Explicit MCP calls**: When you directly reference MCP-enabled features in the IDE

**Detection process:**

1. IDE analyzes user input for agent-related queries
2. Checks available MCP servers for matching capabilities
3. Routes requests to your Raia agent through the configured MCP endpoint
4. Agent processes the request and returns responses through MCP

#### 5. Ask Questions About Agent

**To ask Raia for coding help in your IDE:**

1. **Direct questions in chat**: Type your coding question directly in the IDE's MCP-enabled chat interface
   * "How do I implement a React component for user authentication?"
   * "Can you help me debug this TypeScript error?"
   * "What's the best way to structure this API endpoint?"
2. **Context-aware requests**: The IDE will automatically route to Raia when:
   * You're working on code related to your agent's domain expertise
   * You need help with Raia-specific implementations
   * Your question matches the agent's configured capabilities
3. **Explicit agent reference**: Mention Raia specifically
   * "Raia, can you help me optimize this database query?"
   * "Ask Raia about the best practices for this use case"
