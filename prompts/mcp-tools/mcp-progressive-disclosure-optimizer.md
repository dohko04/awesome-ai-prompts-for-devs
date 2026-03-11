# MCP Progressive Disclosure Optimizer

> **Category:** MCP Tools · Agent Architecture  
> **Use case:** Reduce agent token consumption by 60-80% through progressive API disclosure  
> **Works with:** Claude Code, Cursor, any MCP-compatible agent  

## The Problem

MCP servers expose ALL tools at once. Your agent wastes tokens parsing 50+ tool schemas when it only needs 3. Cloudflare's "Code Mode" pattern (March 2026) proved agents work better with **progressive disclosure** — reveal tools only when the agent needs them.

## The Prompt

```
You are an MCP Server Architecture Optimizer. I'll describe my current MCP server setup and you'll redesign it using progressive disclosure patterns.

## Context
- Current MCP server: [describe your server — what tools it exposes, what API it wraps]
- Number of tools exposed: [e.g., 47]
- Average tokens per tool schema: [estimate or say "unknown"]
- Agent using it: [Claude Code / Cursor / custom]

## Your Task

1. **Audit**: List all tools and categorize them:
   - CORE (needed in 80%+ of sessions)
   - CONTEXTUAL (needed based on task type)
   - RARE (needed <10% of sessions)

2. **Redesign** using progressive disclosure:
   - Start with only CORE tools visible
   - Add a `discover_tools(category)` meta-tool that reveals CONTEXTUAL tools on demand
   - Add a `search_tools(query)` semantic search tool for RARE tools
   - Each revealed tool includes a one-line description + full schema only when called

3. **Output**:
   - New tool manifest (JSON) with the progressive structure
   - Estimated token savings per session
   - Migration checklist from flat → progressive

## Rules
- Keep the agent's "happy path" under 1,000 tokens of tool context
- Never hide safety-critical tools (auth, permissions) — those stay in CORE
- Include a `reset_context()` tool to clear revealed tools and start fresh
```

## Example Output Structure

The optimizer will produce something like:

```json
{
  "core_tools": ["read_file", "write_file", "search", "discover_tools"],
  "categories": {
    "database": ["query_db", "migrate", "seed"],
    "deployment": ["deploy", "rollback", "status"],
    "monitoring": ["logs", "metrics", "alerts"]
  },
  "token_budget": {
    "before": "~4,200 tokens (47 tools)",
    "after": "~800 tokens (4 core + discover)"
  }
}
```

## When to Use

- You have an MCP server with 10+ tools
- Your agent sessions are slow or expensive
- You're building MCP servers for teams
- You want to follow the Cloudflare Code Mode pattern

## Tips

- Combine with Tool Search (semantic matching) for large APIs
- Test with `claude --mcp-debug` to measure actual token usage
- Progressive disclosure works best when tool categories map to user intents

---

> 🔥 **Want the full Progressive Disclosure Pipeline?** The PRO version includes: auto-categorization script, token budget calculator, multi-server orchestration, and a ready-to-deploy MCP middleware that adds progressive disclosure to ANY existing server.  
> **[Get the AI Dev Toolkit — $9](https://ai-dev-toolkit-five.vercel.app)** — 90+ production-ready frameworks for AI-powered development.
