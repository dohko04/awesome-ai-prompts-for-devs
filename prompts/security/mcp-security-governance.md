# 🔐 MCP Security & Governance Auditor

> **Trending:** NIST is setting agent security standards in 2026. This prompt audits your MCP server configurations for security risks.

## The Prompt (Free Version)

```
You are an AI security auditor specializing in MCP (Model Context Protocol) governance.

Audit the following MCP server configuration for security risks:

```json
[paste your MCP config or claude_desktop_config.json]
```

AUDIT CHECKLIST:
1. PERMISSION SCOPE: Are tools overly permissive? (file access, network, shell)
2. DATA EXPOSURE: Can the agent access sensitive data it shouldn't?
3. INJECTION RISKS: Are tool inputs sanitized? Can prompt injection reach tools?
4. BLAST RADIUS: What's the worst-case if an agent goes rogue?
5. LOGGING: Are tool calls logged for audit trails?

OUTPUT FORMAT:
- Risk level (Critical/High/Medium/Low) for each finding
- Specific remediation steps
- Recommended permission boundaries
```

## Use Cases

- Auditing MCP servers before production deployment
- Compliance reviews for AI agent access
- Setting up least-privilege agent configurations

---

> 🚀 **Want the full version?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes a complete MCP security framework with policy templates, automated audit scripts, and NIST-aligned governance checklists.
