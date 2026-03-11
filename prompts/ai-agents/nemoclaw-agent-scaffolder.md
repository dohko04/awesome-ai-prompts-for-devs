# NemoClaw Agent Scaffolder

> Scaffold enterprise AI agents using NVIDIA's NemoClaw architecture (GTC 2026) — open-source, hardware-agnostic, security-first agent deployment for teams.

## Why This Matters Now

NVIDIA is launching **NemoClaw** at GTC 2026 (March 16-19) — an open-source AI agent platform built for enterprise. Unlike OpenClaw (built for individuals), NemoClaw is designed for:

- **Company-wide agent deployment** with built-in security and privacy
- **Hardware-agnostic execution** — runs on any GPU, not just NVIDIA
- **Enterprise guardrails** — prevents the "rogue agent" problems that plagued OpenClaw deployments
- Early partners include Salesforce, Cisco, Google, Adobe, and CrowdStrike

This prompt helps you design agents that align with NemoClaw's architecture before the official SDK drops.

## Prompt

```markdown
You are an Enterprise AI Agent Architect preparing for NVIDIA's NemoClaw platform.

I want to build an AI agent for my organization with these requirements:

**Agent purpose:** {{WHAT_THE_AGENT_DOES}}
**Target users:** {{WHO_USES_IT — role, department, count}}
**Systems it needs access to:** {{APIS_DATABASES_TOOLS}}
**Security requirements:** {{COMPLIANCE_LEVEL — SOC2/HIPAA/internal}}
**Hardware environment:** {{NVIDIA_GPU/AMD/CPU_ONLY/CLOUD}}

Design a NemoClaw-compatible agent scaffold:

1. **Agent Identity & Scope**
   - Define the agent's capabilities and hard boundaries
   - What it CAN do vs. what requires human approval
   - Escalation triggers (when to stop and ask)

2. **Security Architecture**
   - Permission model (least-privilege per action)
   - Data access boundaries — what the agent can read/write
   - Audit trail design (every action logged)
   - Sandboxing strategy (prevent cross-tenant data leaks)

3. **Tool Integration Design**
   - Map each system to a tool definition (NeMo function-calling format)
   - Define input/output schemas for each tool
   - Error handling: what happens when a tool fails?

4. **Deployment Blueprint**
   - Container/pod spec for hardware-agnostic deployment
   - Model selection: which LLM backend for this use case?
   - Scaling strategy: how many concurrent agents per GPU?
   - Monitoring: health checks, latency SLAs, cost tracking

5. **Safety Guardrails**
   - Input validation (reject prompt injection attempts)
   - Output filtering (PII, confidential data)
   - Rate limiting per user/department
   - Kill switch: how to instantly revoke agent access

Provide the complete scaffold as a deployable specification.
```

## Example Use Cases

### IT Helpdesk Agent
```
Agent purpose: Resolve L1 IT tickets (password resets, software installs, VPN issues)
Target users: All employees (~500), triggered via Slack
Systems: Active Directory, Jira Service Management, Okta, Slack API
Security: SOC2 compliant, no access to HR or financial systems
Hardware: Cloud (AWS g5 instances)
```

### Sales Pipeline Assistant
```
Agent purpose: Update CRM, draft follow-up emails, flag stale deals
Target users: Sales team (25 reps), runs continuously
Systems: Salesforce API, Gmail, Google Calendar, Slack
Security: Internal policy — no access to competitor data or pricing overrides
Hardware: NVIDIA A100 on-prem cluster
```

## Limitations of the Free Version

This prompt gives you the scaffolding design pattern. The **[Pro version ($9)](https://dohko04.gumroad.com/l/ai-dev-toolkit)** includes:

- 🏗️ **Full NemoClaw deployment templates** — Docker Compose + Kubernetes manifests
- 🔒 **Enterprise security playbook** — RBAC, audit logging, PII filtering pipeline
- ⚡ **Multi-agent orchestration** — coordinate 3+ NemoClaw agents with handoff protocols
- 📊 **Cost modeling calculator** — GPU hours, token costs, and ROI projections per agent
- 🧪 **Agent evaluation framework** — test suites for safety, accuracy, and latency

---

*Part of the [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) — 90+ production-ready AI/dev resources for $9.*
