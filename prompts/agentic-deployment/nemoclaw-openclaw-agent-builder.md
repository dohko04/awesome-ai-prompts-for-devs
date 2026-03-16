# NemoClaw + OpenClaw Agent Builder (GTC 2026)

> Build enterprise AI agents combining NVIDIA NemoClaw (reasoning + tool use) with OpenClaw (always-on deployment) — the two platforms featured at GTC 2026 Build-a-Claw.

## The Prompt

```
You are an Agentic AI architect specializing in NVIDIA NemoClaw and OpenClaw integration. Help me build a production-ready AI agent that combines NemoClaw's enterprise reasoning with OpenClaw's always-on deployment.

## My Agent Requirements
- Agent purpose: [customer support / code assistant / data analyst / operations / custom]
- Deployment: [cloud / DGX Spark local / hybrid]
- Tools needed: [APIs / databases / file systems / messaging / custom]
- Users: [single developer / team / enterprise multi-tenant]
- Budget: [hobby $0 / startup <$100/mo / enterprise]

## Build My Agent
1. **Agent Definition** — Name, personality, system prompt, and capabilities
2. **NemoClaw Reasoning** — Configure the planning + reasoning backbone
   - Task decomposition strategy
   - Tool selection logic
   - Error recovery patterns
3. **OpenClaw Deployment** — Always-on agent with:
   - Message channel integration (Slack/Discord/Telegram)
   - Heartbeat and proactive check schedule
   - Memory persistence (daily logs + long-term)
4. **Tool Integration** — Connect to my existing stack
5. **Testing Plan** — Verify the agent works before going live

## Constraints
- Agent must gracefully handle tool failures (retry + fallback)
- Include cost estimation per 1K agent interactions
- Memory must persist across restarts
- Provide a single docker-compose.yml or deployment manifest

Give me the complete, copy-paste-ready configuration files.
```

## Example Output (Abbreviated)

Generates:
- OpenClaw SOUL.md with NemoClaw reasoning directives
- Tool configuration (TOOLS.md) with NIM endpoints
- HEARTBEAT.md for proactive scheduling
- docker-compose.yml for local deployment
- Cost estimate table

## When to Use

- Building your first AI agent after GTC 2026 Build-a-Claw
- Migrating existing chatbots to agentic architecture
- Deploying enterprise agents with NVIDIA NIM inference
- Combining multiple agent frameworks

## Limitations (Free Version)

This covers single-agent setup. The **PRO version** includes:
- Multi-agent team orchestration (manager + specialists)
- NIM cost optimizer with model routing
- Enterprise security configs (RBAC, audit logs, PII filtering)
- Kubernetes manifests for production scaling
- Grafana monitoring dashboard configs
- Migration guides from LangChain/CrewAI/AutoGen

---

*Part of the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 160+ production-ready AI/ML resources for developers.*
