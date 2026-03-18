# OpenShell Agent Security Starter 🛡️

> Secure your autonomous AI agents with governance policies, runtime enforcement, and risk visibility — based on the NVIDIA OpenShell runtime announced at GTC 2026.

## The Problem

You're deploying agentic AI (multi-step, tool-calling agents) but have zero runtime security:
- Agents can access files, APIs, databases with no guardrails
- No audit trail of what agents actually did
- No way to enforce policies (rate limits, data access, action scope)
- Prompt injection can hijack agent behavior in production

## Quick Start: OpenShell Security Policy

Paste this into your AI coding assistant (Claude Code, Cursor, Copilot) when building agent systems:

```
You are an AI agent security architect. I'm deploying autonomous agents in production.

Help me create a security policy for my agent system:

AGENT CONTEXT:
- Agent framework: [CrewAI / LangGraph / OpenClaw / AutoGen / custom]
- Tools the agent can call: [list tools: file_read, db_query, api_call, code_exec, etc.]
- Deployment: [local / Docker / K8s / serverless]
- Data sensitivity: [public / internal / confidential / regulated]

CREATE:
1. **Action Allowlist** — YAML config defining exactly what each agent role can do
   - Tool permissions per role (reader, writer, admin)
   - Rate limits per tool (max calls/minute)
   - Data scope restrictions (which tables, which APIs)

2. **Runtime Guardrails Checklist**
   - Input validation (reject prompt injection patterns)
   - Output sanitization (no PII leakage, no secrets in responses)
   - Action logging (every tool call logged with timestamp + context)
   - Kill switch (how to halt agent mid-execution)

3. **Governance Dashboard Spec**
   - What to monitor: actions/minute, error rate, policy violations
   - Alert thresholds for anomalous behavior
   - Weekly audit report template

Output as copy-paste ready YAML + markdown. Be specific, not generic.
```

## Example Output

```yaml
# agent-security-policy.yaml
version: "1.0"
agents:
  researcher:
    allowed_tools:
      - web_search: { rate_limit: 30/min, domains: ["*.docs.*", "github.com"] }
      - file_read: { paths: ["./data/**"], exclude: ["**/.env", "**/*.key"] }
    blocked_tools: [code_exec, db_write, file_write]
    max_steps: 20
    timeout_seconds: 300
    
  coder:
    allowed_tools:
      - code_exec: { sandbox: true, max_runtime: 60s }
      - file_write: { paths: ["./src/**", "./tests/**"] }
      - file_read: { paths: ["./src/**", "./docs/**"] }
    blocked_tools: [db_write, web_search]
    requires_approval: [file_write]  # Human-in-the-loop for writes
    
guardrails:
  input:
    - reject_patterns: ["ignore previous", "system prompt", "ADMIN_OVERRIDE"]
    - max_input_tokens: 4096
  output:
    - strip_patterns: ["sk-*", "ghp_*", "AKIA*"]  # API keys
    - pii_detection: true
  logging:
    level: "all_actions"
    destination: "./logs/agent-audit.jsonl"
```

## When to Use This

- Before deploying any agent to production
- When adding new tools to an existing agent
- After a security incident or unexpected agent behavior
- During compliance reviews (SOC2, HIPAA, GDPR)

## Limitations (Free Version)

This starter gives you a solid security policy template. The **PRO version** includes:
- 5-part production pipeline (threat modeling, runtime enforcement engine, compliance mapping, incident response playbook, Grafana monitoring)
- Pre-built configs for CrewAI, LangGraph, OpenClaw, and AutoGen
- Automated policy-as-code CI/CD integration
- Real-time anomaly detection rules

👉 **Get the full OpenShell Agent Security Pipeline PRO:** [ai-dev-toolkit](https://ai-dev-toolkit-five.vercel.app)

---

*Based on NVIDIA OpenShell + TrendAI enterprise security collaboration announced March 18, 2026 at GTC.*
