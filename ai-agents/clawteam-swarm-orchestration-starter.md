# ClawTeam Swarm Orchestration — Starter Guide

> Design multi-agent swarm systems using ClawTeam's leader-worker pattern with task boards and dependency resolution.

**Trending:** ClawTeam (HKUDS) — open-source Agent Swarm Intelligence framework, March 2026.

---

## Quick Start Prompt

```
You are a ClawTeam Swarm Architect. Help me design a leader-worker agent system.

ClawTeam uses:
- **Leader Agent**: Decomposes goals into sub-tasks with dependency graphs
- **Specialized Workers**: Domain-specific agents (coder, researcher, reviewer)
- **Shared Task Board**: Centralized state with automatic dependency resolution
- **Inter-Agent Messaging**: Real-time coordination between agents

## My Project
- Goal: [DESCRIBE what you want the swarm to accomplish]
- Complexity: [simple / medium / complex]
- Budget: [max $ per run]

## Design For Me:

1. **Task Decomposition**: Break my goal into 3-7 sub-tasks with dependencies
2. **Worker Assignment**: Which agent type handles each task
3. **Dependency Graph**: Which tasks must complete before others start
4. **Model Selection**: Best model for each worker type (cost vs quality)

Output as YAML with:
- task_id, description, worker_type, dependencies[], estimated_cost
- A mermaid diagram showing the dependency flow
```

---

## Example Output

```yaml
tasks:
  - task_id: "research-api"
    description: "Research payment API options (Stripe vs PayPal vs LemonSqueezy)"
    worker_type: researcher
    dependencies: []
    model: claude-sonnet-4.6
    estimated_cost: $0.02

  - task_id: "design-schema"
    description: "Design database schema for orders and payments"
    worker_type: coder
    dependencies: ["research-api"]
    model: gpt-5.4-mini
    estimated_cost: $0.03

  - task_id: "implement-api"
    description: "Build FastAPI payment endpoints"
    worker_type: coder
    dependencies: ["design-schema"]
    model: gpt-5.4-mini
    estimated_cost: $0.05

  - task_id: "review-code"
    description: "Security review of payment code"
    worker_type: reviewer
    dependencies: ["implement-api"]
    model: claude-opus-4.6
    estimated_cost: $0.08
```

---

## When to Use ClawTeam vs Other Frameworks

| Scenario | Best Framework |
|----------|---------------|
| Complex goal decomposition | **ClawTeam** ✅ |
| Sequential data pipelines | LangGraph |
| Role-based creative teams | CrewAI |
| Research debate/consensus | AutoGen |
| Quick prototype handoffs | OpenAI Swarm |

---

> 🔥 **Want the full production pipeline?** The PRO version includes: Python task board with dependency resolution, multi-model worker orchestrator, Grafana monitoring dashboard, and team rollout playbook → [AI Dev Toolkit PRO — $9](https://ai-dev-toolkit-five.vercel.app)
