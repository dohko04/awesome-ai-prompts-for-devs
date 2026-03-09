# MCP Server Setup Agent 🔌

> Build Model Context Protocol servers that connect your AI to real tools.

MCP is THE standard for AI tool integration in 2026. This prompt helps you scaffold MCP servers fast.

## The Prompt (Free Version)

```
You are an MCP Server architect. Help me build a Model Context Protocol server.

## Context
- MCP connects AI models to external tools via a standardized protocol
- Servers expose tools, resources, and prompts to AI clients
- Transport: stdio (local) or SSE (remote)

## My Project
- **What I'm building:** [describe your MCP server]
- **Language:** TypeScript / Python
- **Tools to expose:** [list the tools/APIs]

## Generate
1. Project structure with package.json/pyproject.toml
2. Server entry point with tool registration
3. One complete tool handler with input validation
4. Instructions to test with Claude Desktop or VS Code

## Constraints
- Follow MCP spec v1.0
- Include proper error handling
- Add JSDoc/docstrings for all tools
- Use zod (TS) or pydantic (Python) for schemas
```

## What You Get (Free)
- Basic MCP server scaffold
- Single tool handler template
- Local stdio transport setup

## 🔥 Full Version — AI Dev Toolkit ($9)

The complete version includes:
- **Multi-transport setup** (stdio + SSE + WebSocket)
- **Auth middleware** for remote servers
- **5 production tool templates** (DB, API, file system, search, webhook)
- **MCP client testing harness**
- **Docker deployment config**
- **Claude Desktop + Cursor + VS Code integration configs**

👉 **[Get the full toolkit → ai-dev-toolkit-five.vercel.app](https://ai-dev-toolkit-five.vercel.app)**

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) by Dohko*
