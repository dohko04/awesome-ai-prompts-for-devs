# MCP Tool Connector Generator 🔗

> Generate a complete MCP (Model Context Protocol) server that connects your AI assistant to any API or service. Copy-paste the output and run it.

**Why this matters:** MCP has 97M+ SDK downloads and Linux Foundation backing. It's the universal standard for connecting AI coding agents to external tools. Every major IDE supports it (Cursor, VS Code, Claude Code, Windsurf).

## The Prompt (Free Version)

```
You are an MCP Server Engineer. Generate a complete, working MCP server that connects an AI assistant to an external service.

## What I Want to Connect
- **Service/API:** [e.g., "my PostgreSQL database", "Stripe API", "internal REST API at api.example.com"]
- **Operations needed:** [e.g., "read users, create orders, check payment status"]
- **Auth method:** [e.g., "API key in header", "Bearer token", "database connection string"]
- **Language:** TypeScript (default) or Python

## Generate a Complete MCP Server

### Requirements:
1. **package.json** (or pyproject.toml) with all dependencies
2. **src/index.ts** (or server.py) — the full server implementation
3. **Tool definitions** with proper JSON Schema for parameters
4. **Error handling** — graceful failures, not crashes
5. **Client config** — the JSON snippet to add to Cursor/Claude/VS Code settings

### MCP Server Must Include:
- `server.setRequestHandler(ListToolsRequestSchema, ...)` — list available tools
- `server.setRequestHandler(CallToolRequestSchema, ...)` — execute tools
- Proper TypeScript types or Python type hints
- Input validation before calling external APIs
- Meaningful error messages the AI can understand

### Tool Design Principles:
- Each tool does ONE thing well
- Parameter descriptions help the AI know what to pass
- Return structured data (JSON), not raw HTML
- Include a "health check" or "list" tool for the AI to verify connection

### Client Configuration (generate for all):
```json
// For Cursor (.cursor/mcp.json)
{
  "mcpServers": {
    "my-service": {
      "command": "npx",
      "args": ["tsx", "src/index.ts"],
      "env": { "API_KEY": "your-key-here" }
    }
  }
}
```

## Output Format
Generate the complete project as a single copyable codeblock per file, with clear file paths. Ready to `npm install && npm start`.
```

## What You Get

A working MCP server you can run in 60 seconds:

```bash
mkdir my-mcp-server && cd my-mcp-server
# paste the generated files
npm install
# add config to your AI tool
# done — your AI can now talk to your service
```

---

## 🔒 Want More?

The **[AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)** ($9) includes:
- **12 pre-built MCP server templates** (PostgreSQL, MongoDB, Stripe, GitHub, Slack, Notion, REST generic, GraphQL, S3, Redis, Supabase, Firebase)
- **Multi-service orchestrator** — one MCP server that connects to multiple APIs
- **Security hardening prompt** — rate limiting, input sanitization, auth token rotation
- **MCP testing framework** — validate your server works before connecting to AI
- **100+ battle-tested prompts** for every stage of development

[**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
