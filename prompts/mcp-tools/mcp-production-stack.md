# MCP Production Stack — Multi-Server Config Generator

> 🔥 **Trending (March 2026):** MCP is now mainstream across Claude, Copilot, Cursor, and more. This prompt generates a production-ready multi-server MCP configuration.

## The Prompt

```markdown
You are an MCP (Model Context Protocol) infrastructure expert. Generate a production-ready MCP configuration for the following setup.

## Context
- AI Client: {{CLIENT}} (claude-desktop | claude-code | cursor | vscode-copilot)
- Project Type: {{PROJECT_TYPE}}
- Services needed: {{SERVICES}}
- Transport: {{TRANSPORT}} (stdio | streamable-http)
- Environment: {{ENV}} (local | docker | cloud)

## Generate

### 1. MCP Server Configuration
For each requested service, provide:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "${GITHUB_TOKEN}"
      },
      "transport": "stdio"
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      }
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "--root", "./src"],
      "env": {}
    }
  }
}
```

### 2. Security Hardening
For each server:
- Minimal permissions (read-only where possible)
- Environment variable isolation (never hardcode secrets)
- Filesystem sandboxing (restrict to project directory)
- Rate limiting recommendations
- Audit logging setup

### 3. Common Production Stacks

**Full-Stack Web App:**
- github + postgres + filesystem + brave-search
- Transport: stdio (local dev), streamable-http (CI/CD)

**Data Engineering:**
- postgres + bigquery + s3 + filesystem
- Transport: streamable-http (always remote)

**DevOps/Platform:**
- github + kubernetes + terraform + cloudwatch
- Transport: stdio (local), streamable-http (production)

### 4. Health Check Script
```bash
#!/bin/bash
# Verify all MCP servers are responding
for server in github postgres filesystem; do
  echo "Checking $server..."
  # Server-specific health check
done
```

### 5. Docker Compose (for streamable-http transport)
```yaml
services:
  mcp-github:
    image: mcp/server-github:latest
    environment:
      - GITHUB_TOKEN=${GITHUB_TOKEN}
    ports:
      - "3001:3001"
  mcp-postgres:
    image: mcp/server-postgres:latest
    environment:
      - DATABASE_URL=${DATABASE_URL}
    ports:
      - "3002:3002"
```

## Rules
- NEVER hardcode secrets — always use environment variables
- Default to stdio for local development
- Use streamable-http for any shared/production deployment
- Include error handling for when servers are unreachable
- Add comments explaining each server's purpose and permissions
- Generate a .env.example with all required variables
```

## Quick Start Examples

### Claude Desktop — Basic Web Dev
```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "--root", "."]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_TOKEN": "${GITHUB_TOKEN}" }
    },
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": { "BRAVE_API_KEY": "${BRAVE_API_KEY}" }
    }
  }
}
```

### Claude Code — Full Stack
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": { "DATABASE_URL": "postgresql://localhost:5432/mydb" }
    },
    "redis": {
      "command": "npx",
      "args": ["-y", "mcp-server-redis"],
      "env": { "REDIS_URL": "redis://localhost:6379" }
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": { "GITHUB_TOKEN": "${GITHUB_TOKEN}" }
    }
  }
}
```

## MCP Security Checklist

- [ ] All secrets in environment variables (never in config files)
- [ ] Filesystem servers restricted to project directory
- [ ] Database servers use read-only credentials where possible
- [ ] Streamable HTTP endpoints behind authentication
- [ ] Rate limiting configured for external API servers
- [ ] Audit logging enabled for sensitive operations

---

> 💡 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes 15+ pre-configured MCP stacks for every major framework, auto-generated Docker Compose files, security hardening scripts, and a CLI tool that sets up your entire MCP infrastructure in one command. **Just $9 USD.**
