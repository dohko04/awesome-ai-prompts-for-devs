# API Gateway AI Agent Controller (FREE)

> Quick setup guide for using API gateways as control layers for AI agents. Based on the March 2026 industry shift: Kong and Apigee now support MCP tools as first-class API products.

## Why This Matters

AI agents make autonomous API calls. Without gateway controls, one rogue agent can burn your entire API budget, access unauthorized endpoints, or make untraceable external calls.

## Quick Architecture

```
Agent → API Gateway → MCP Server / API
         ↓
    Auth + Rate Limit + Logging + Cost Tracking
```

## Basic Kong Setup for Agent Control

```yaml
# docker-compose.yml — Kong gateway for AI agents
version: "3.8"
services:
  kong:
    image: kong/kong-gateway:3.9
    environment:
      KONG_DATABASE: "off"
      KONG_DECLARATIVE_CONFIG: /kong/kong.yaml
      KONG_PROXY_LISTEN: "0.0.0.0:8000"
      KONG_ADMIN_LISTEN: "0.0.0.0:8001"
    ports:
      - "8000:8000"
      - "8001:8001"
    volumes:
      - ./kong.yaml:/kong/kong.yaml

# kong.yaml — Minimal agent gateway config
# _format_version: "3.0"
# services:
#   - name: mcp-tools
#     url: http://mcp-server:3000
#     routes:
#       - name: mcp-route
#         paths: ["/mcp"]
#     plugins:
#       - name: key-auth
#       - name: rate-limiting
#         config: { minute: 30 }
#       - name: http-log
#         config: { http_endpoint: "http://logger:8080/audit" }
```

## Agent Configuration Checklist

```yaml
agent_gateway_checklist:
  per_agent:
    - "Unique API key (never shared between agents)"
    - "Rate limit appropriate to role (research=60/min, ops=10/min)"
    - "Tool access list (which MCP tools can this agent call?)"
    - "Daily budget cap in USD"
  
  per_tool:
    - "Rate limit per tool (database writes stricter than reads)"
    - "Request size limit"
    - "Response filtering (redact PII before returning to agent)"
  
  monitoring:
    - "Log every agent→tool call with agent ID + timestamp"
    - "Alert on budget >80% usage"
    - "Alert on unusual call patterns (10x normal volume)"
    - "Weekly cost attribution report"
```

## Decision Matrix

| Agents | Tools | Gateway Needed? |
|--------|-------|----------------|
| 1 agent | 1-3 tools | ❌ Direct is fine |
| 2-5 agents | Shared APIs | ✅ Basic gateway |
| 5+ agents | Production APIs | ✅ Full gateway + monitoring |
| Any | External paid APIs | ✅ Always (cost control) |

---

## 🔥 Want the Full Pipeline?

The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes the **API Gateway Agent Controller Pipeline PRO** with:

- **Kong MCP plugin configuration** — Complete YAML for multi-agent, multi-tool gateway with RBAC
- **Cost attribution engine** — Python middleware tracking per-agent, per-tool costs with budget enforcement
- **Grafana monitoring dashboard** — 6-panel real-time dashboard for agent traffic, costs, and security events
- **Agent-to-gateway migration checklist** — 4-phase, 2-3 day migration from direct API calls to controlled gateway
- **Apigee + AWS API Gateway configs** — Multi-cloud gateway templates

→ Part of **200+ production-ready AI developer resources** for $9 USD.
