# 🔧 MCP Server Builder

Generate a complete MCP (Model Context Protocol) server that exposes your API, database, or service as tools that any AI assistant can use.

## The Prompt

```
You are an MCP Server expert. Build a complete MCP server for: {SERVICE_DESCRIPTION}

Requirements:
- Language: {LANGUAGE: TypeScript | Python}
- Transport: {TRANSPORT: stdio | SSE | streamable-http}
- Tools to expose: {TOOLS_LIST}

For each tool, generate:

1. **Tool Definition**:
   - name: snake_case, descriptive
   - description: clear enough for an LLM to know when to use it
   - inputSchema: JSON Schema with all parameters, types, and descriptions
   
2. **Handler Implementation**:
   - Input validation
   - Error handling with meaningful messages
   - Proper response formatting (text content for simple results, structured data for complex)

3. **Server Setup**:
   - All imports and dependencies
   - Server initialization with name and version
   - Tool registration
   - Transport configuration
   - Graceful shutdown handling

4. **Configuration**:
   - package.json or pyproject.toml with dependencies
   - MCP client config snippet (for claude_desktop_config.json or Cursor settings)
   - Environment variables for API keys/secrets

5. **Testing**:
   - Example tool calls with expected responses
   - Edge cases to handle

Output a complete, runnable project structure.

Service: {SERVICE_DESCRIPTION}
Tools: {TOOLS_LIST}
Language: {LANGUAGE}
Auth needed: {AUTH: none | API key | OAuth}
```

## Example

```
Service: GitHub issue tracker — read, create, update, and search issues
Tools: list_issues, create_issue, update_issue, search_issues, get_issue_comments
Language: TypeScript
Auth: API key (GitHub personal access token)
```

## Key MCP Concepts

- **Tools**: Functions the AI can call (like API endpoints)
- **Resources**: Data the AI can read (like files or DB records)
- **Prompts**: Pre-built prompt templates the AI can use
- **Transport**: How client and server communicate (stdio for local, SSE/HTTP for remote)

---

> 🏗️ **Skip the boilerplate.** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) includes ready-to-deploy MCP servers for GitHub, databases, Slack, Notion, and more — plus advanced patterns for auth, rate limiting, caching, and multi-server orchestration.
