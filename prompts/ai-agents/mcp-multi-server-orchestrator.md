# 🔌 MCP Multi-Server Orchestrator

> Design and generate a complete MCP (Model Context Protocol) multi-server setup for AI-powered development workflows. Works with Claude Code, Cursor, Windsurf, and any MCP-compatible tool.

## The Prompt

```
You are an MCP infrastructure architect. Help me design a production-ready multi-server MCP configuration.

## My Setup
- **AI Tool**: [Claude Code / Cursor / Windsurf / Other]
- **Project type**: [web app / API / CLI / monorepo / mobile]
- **Tech stack**: [e.g., TypeScript, Python, React, PostgreSQL]
- **Services I use**: [e.g., GitHub, Vercel, Supabase, AWS, Linear, Slack]
- **Local tools**: [e.g., Docker, PostgreSQL, Redis]

## What I Need

### 1. MCP Server Inventory
Analyze my stack and recommend MCP servers in 3 tiers:
- **Essential** (install immediately): servers that 10x my daily workflow
- **Recommended** (install this week): nice productivity boosts
- **Optional** (install later): situational but powerful

For each server provide:
- Package name and install command
- What it enables (specific use cases)
- Security considerations (what access it needs)
- Estimated token cost impact (low/medium/high)

### 2. Configuration File
Generate the complete MCP config file for my AI tool:
- For Claude Code: `.claude/mcp.json`
- For Cursor: `.cursor/mcp.json`
- For VS Code: `.vscode/mcp.json`

Include:
- Server definitions with args and env vars
- Tool whitelisting (only expose what's needed)
- Environment-specific configs (dev vs staging vs prod)

### 3. Security Hardening
- Which servers should run in sandbox mode
- Environment variables that should NEVER be in config files
- Read-only vs read-write access per server
- Network isolation recommendations

### 4. Custom MCP Server Starter
If I need a custom server (for internal APIs, databases, etc.), generate a starter template:
- TypeScript MCP server skeleton
- 2-3 example tools relevant to my stack
- Proper error handling and input validation
- README with setup instructions

## Output Format
1. Server recommendation table (tier, name, purpose, install)
2. Complete config JSON file
3. `.env.example` with required environment variables
4. Security checklist
5. (Optional) Custom server starter code
```

## When to Use

- Starting a new project and want AI tooling from day one
- Upgrading from basic AI coding to full MCP-powered workflows
- Auditing your MCP setup for security and efficiency
- Building custom MCP servers for internal tools

## Pro Tips

- **Token budget**: Each MCP server adds tool descriptions to your context. Keep it under 40 tools total (Cursor hard limit) or use tool search (Claude Code)
- **Security first**: Never put API keys in `mcp.json` — always use env vars
- **Start small**: 3-4 servers > 15 servers. Add when you feel the pain, not before
- **Custom servers are easy**: A basic MCP server is ~50 lines of TypeScript

## Example Output (Partial)

```json
// .claude/mcp.json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      },
      "tools": ["query", "list_tables", "describe_table"]
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "--root", "./src"],
      "sandbox": true
    },
    "vercel": {
      "command": "npx",
      "args": ["-y", "mcp-vercel"],
      "env": {
        "VERCEL_TOKEN": "${VERCEL_TOKEN}"
      },
      "tools": ["list_deployments", "get_deployment", "list_projects"]
    }
  }
}
```

```
# .env.example
GITHUB_TOKEN=ghp_xxxxxxxxxxxx      # repo, read:org scopes
DATABASE_URL=postgresql://...       # read-only connection recommended
VERCEL_TOKEN=xxxxxxxxxxxx           # from vercel.com/account/tokens
```

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs)*

> 🚀 **Want 20+ pre-built MCP configs for every stack + custom server templates?** [Get the Full Toolkit →](https://ai-dev-toolkit-five.vercel.app)
