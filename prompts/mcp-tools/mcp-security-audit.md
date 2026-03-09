# 🔐 MCP Server Security Audit

> Audit your MCP server implementation against OWASP guidelines and common vulnerability patterns. Covers input validation, auth flows, tool poisoning, and data exfiltration risks.

## The Prompt

```markdown
You are an MCP (Model Context Protocol) security specialist. Audit my MCP server code for vulnerabilities following OWASP's secure MCP development guidelines.

## Context
- **MCP Server Code:** [paste your server code or describe the tools/resources it exposes]
- **Transport:** [stdio | SSE | streamable HTTP]
- **Auth Method:** [OAuth 2.0 | API key | none]
- **Deployment:** [local | remote | cloud function]

## Audit Checklist — Analyze Each:

### 1. Input Validation & Injection
- Are all tool parameters validated with strict schemas (zod, JSON Schema)?
- Can a malicious prompt inject unexpected tool calls?
- Are file paths, URLs, and SQL inputs sanitized?

### 2. Tool Poisoning & Prompt Injection
- Could a compromised resource inject hidden instructions into tool descriptions?
- Are tool descriptions static or dynamically generated (dynamic = risk)?
- Is there separation between system-level and user-level tool access?

### 3. Authentication & Authorization
- Is OAuth 2.0 with PKCE used for remote transports?
- Are scopes properly defined per tool (least privilege)?
- Can one user's session access another user's resources?

### 4. Data Exfiltration
- Can tools be chained to read sensitive data then send it externally?
- Are outbound network calls restricted or logged?
- Is there a content filter on tool responses?

### 5. Rate Limiting & Resource Abuse
- Are expensive operations (DB queries, API calls) rate-limited?
- Is there a timeout on long-running tools?
- Can recursive tool calls create infinite loops?

### 6. Logging & Observability
- Are all tool invocations logged with caller identity?
- Are sensitive parameters (tokens, PII) redacted in logs?
- Is there an audit trail for resource access?

## Output Format
For each finding:
- **Severity:** Critical / High / Medium / Low
- **Category:** (from checklist above)
- **Finding:** What's wrong
- **Risk:** What could happen
- **Fix:** Specific code change or configuration

End with a security score (0-100) and top 3 priority fixes.
```

## When to Use

- Before deploying an MCP server to production
- When adding new tools that access sensitive data (DBs, APIs, file systems)
- After the OWASP MCP security guide dropped — this prompt operationalizes it
- During security reviews of AI-integrated systems

## Pro Tips

- Run this audit every time you add a new tool to your MCP server
- Pay special attention to **tool poisoning** — it's the #1 novel attack vector in MCP
- For remote MCP servers, OAuth 2.0 with PKCE is non-negotiable
- Combine with the `mcp-server-builder.md` prompt to build secure servers from scratch

## Example Use Cases

- Auditing a GitHub MCP server that exposes repo management tools
- Reviewing a database MCP server before connecting it to Claude/Cursor
- Checking a multi-tenant MCP server for session isolation issues

---

> 💡 **Want the full security toolkit?** The complete AI Dev Toolkit includes MCP penetration testing prompts, secure server templates, and auth flow generators.
>
> **[Get 100+ prompts like this → AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)**
