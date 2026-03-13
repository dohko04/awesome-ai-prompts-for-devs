# AI Agent Incident Response Playbook

> When your AI agent breaks production — a structured response framework. Based on real incidents (Amazon March 2026: agent followed stale wiki, crashed retail site).

## The Prompt

```markdown
You are an AI agent incident response specialist. Help me build a response playbook for when AI agents cause production incidents.

## Context
I'm building/deploying AI agents that [DESCRIBE YOUR AGENTS: e.g., "interact with internal tools, query knowledge bases, execute automated workflows"]. I need a framework to prevent, detect, and respond to agent-caused incidents.

## Incident Classification

### Severity Levels for Agent Failures
- **P0 — Agent caused customer-facing outage** (e.g., agent acted on stale/wrong data)
- **P1 — Agent produced incorrect output consumed by humans** (e.g., wrong recommendations)
- **P2 — Agent consumed excessive resources** (e.g., infinite loops, token storms)
- **P3 — Agent behaved unexpectedly but no user impact** (e.g., hallucinated in logs)

## Pre-Incident Checklist
For my specific setup, evaluate:

1. **Knowledge Freshness** — How old can the agent's knowledge sources be before they become dangerous?
2. **Action Boundaries** — What actions can the agent take? Which are reversible vs. irreversible?
3. **Human Checkpoints** — Where must a human approve before the agent acts?
4. **Circuit Breakers** — What thresholds trigger automatic agent shutdown?
5. **Rollback Plan** — Can the agent's actions be undone? How fast?

## Response Template
When an incident happens, walk me through:
1. **Detect** — What signals indicate the agent failed?
2. **Isolate** — How to stop the agent immediately
3. **Assess** — What damage occurred, what data was affected
4. **Recover** — Steps to restore correct state
5. **Review** — Root cause analysis specific to agent failures

## Output Format
Give me a practical, copy-paste-ready runbook with specific commands/steps for my stack.
Focus on the unique failure modes of AI agents (stale knowledge, hallucination, action loops)
vs. traditional software bugs.
```

## When to Use

- Setting up AI agents in production for the first time
- After an agent-caused incident (post-mortem framework)
- Building guardrails before deploying autonomous agents
- Team training on AI agent failure modes

## Example Output

The prompt generates a customized runbook covering:
- Agent-specific monitoring alerts
- Kill switches and circuit breaker configs
- Knowledge source freshness validation
- Post-incident review template focused on agent behavior

## Tips

- Be specific about your agent's capabilities — the more detail, the better the playbook
- Run this BEFORE your first incident, not after
- Update the playbook after every real incident

---

> 💡 **Want the full production version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) PRO includes: multi-agent incident correlation, automated stale knowledge detection, circuit breaker configs for 5 agent frameworks, cost-aware shutdown triggers, and team escalation workflows. Worth every penny if you're running agents in production.
