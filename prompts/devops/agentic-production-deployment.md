# 🚀 Agentic AI Production Deployment Prompt

> Design production-ready deployment patterns for AI agents with observability, fallbacks, and state management.

## The Prompt

```
You are an AI Infrastructure Engineer specializing in deploying agentic AI systems to production. Help me design a robust deployment architecture.

## Context
- Agent framework: [LangGraph / CrewAI / AutoGen / custom]
- Agent type: [single agent / multi-agent / human-in-the-loop]
- Infrastructure: [AWS / GCP / Azure / self-hosted]
- Scale: [<100 req/day / 100-10K / 10K+ requests/day]
- Current stage: [prototype / staging / production]

## Tasks

### 1. Agent Architecture Review
Analyze my agent setup and recommend:
- State management strategy (checkpointing, persistence)
- Error handling patterns (retries, fallbacks, circuit breakers)
- Tool call sandboxing (prevent destructive actions)
- Memory architecture (short-term vs long-term, eviction policies)

### 2. Deployment Pattern
Design the deployment infrastructure:
- Container orchestration setup (Docker + K8s manifests)
- Queue-based async execution for long-running agents
- Health checks specific to agent workloads
- Graceful degradation when LLM providers have outages
- Blue/green or canary deployment for agent updates

### 3. Observability Stack
Set up monitoring for agentic workloads:
- Trace each agent step (tool calls, LLM invocations, decisions)
- Log structured data: input → reasoning → tool calls → output
- Alert on: stuck agents, excessive tool loops, cost spikes
- Dashboard metrics: completion rate, avg steps per task, cost per task

### 4. Safety & Governance
- Human approval gates for high-risk actions
- Audit trail for all agent decisions
- Cost caps and kill switches
- Rollback procedures for bad agent behavior

Output concrete configs, manifests, and code — not just theory.
```

## When to Use
- Moving AI agents from prototype to production
- Designing infrastructure for multi-agent systems
- Setting up monitoring for autonomous AI workflows
- After an agent caused an incident in production

## Key Patterns Covered
- **Circuit Breaker**: Stop agent loops before they burn tokens
- **Checkpoint/Resume**: Persist agent state for long-running tasks
- **Human-in-the-Loop Gates**: Pause for approval on risky actions
- **Graceful Degradation**: Fallback to simpler logic when LLMs fail

## Tips
- Always set max iterations and cost caps on agents
- Log every tool call with inputs/outputs for debugging
- Start with human-in-the-loop, remove gates gradually as trust builds
- Test agent behavior with adversarial inputs before production

---

> 🔥 **Want complete Kubernetes manifests, Terraform modules, pre-built observability dashboards (Grafana + Datadog), and battle-tested agent deployment pipelines?** Check out [AI Dev Toolkit PRO](https://dohko04.gumroad.com/l/ai-dev-toolkit)

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs)*
