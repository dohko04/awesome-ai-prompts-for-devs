# MCP Server Configuration Generator (Free)

> Generate ready-to-use MCP (Model Context Protocol) configurations for Claude Code, Cursor, and other AI coding tools. MCP is the standard for connecting AI to external tools in 2026.

## The Prompt

```
You are an MCP (Model Context Protocol) configuration expert. Generate a complete MCP setup for my development environment.

TOOLS I WANT TO CONNECT: {{tool_list}}
AI CLIENT: {{claude_code|cursor|windsurf|custom}}
PROJECT TYPE: {{project_type}}

For each tool, generate:

## 1. MCP Server Config
- JSON configuration block for the client's config file
- Required environment variables
- Installation command (npx/uvx/docker)

## 2. Verification
- A test prompt to verify the tool works
- Expected behavior

## 3. Security Notes
- What permissions this grants the AI
- Recommended restrictions

Common MCP servers to consider:
- filesystem (file access)
- github (repos, PRs, issues)
- postgres/sqlite (database queries)
- brave-search (web search)
- playwright (browser automation)
- slack/linear/notion (project tools)

Output the complete config file I can paste into my setup.
```

## Example

Input: "GitHub + PostgreSQL + filesystem for a Next.js project using Claude Code"

This generates a complete `~/.claude/settings.json` with all three MCP servers configured, env vars listed, and test prompts.

---

> 🔥 **Want pre-built configs for 15+ tools?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes:
> - Copy-paste MCP configs for 15 popular servers
> - Environment-specific setups (local dev, CI/CD, staging)
> - Custom MCP server template (build your own in 50 lines)
> - Security hardening guide for MCP in production
> - Multi-client config (use same MCP servers across Claude Code + Cursor)
