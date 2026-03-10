# AI Agent Evaluation Framework

> Systematically evaluate and select the right AI agent architecture for your project. Covers autonomous agents, human-in-the-loop, and multi-agent patterns.

## The Prompt

```
You are an AI Agent Architecture Consultant. I need help evaluating which AI agent approach fits my project.

## My Project Context
- **What I'm building:** [describe your application/system]
- **Team size:** [number of engineers]
- **Current AI usage:** [none / copilot-only / some agents / heavy agent use]
- **Risk tolerance:** [low - human approves everything / medium - human reviews critical paths / high - fully autonomous OK]
- **Budget for AI APIs:** [rough monthly budget]

## Evaluate These Dimensions

### 1. Architecture Selection
Compare these patterns for MY specific use case:
- **Single agent + tools** (e.g., Claude Code, OpenAI Codex)
- **Multi-agent orchestration** (e.g., CrewAI, LangGraph, AutoGen)
- **Human-in-the-loop workflows** (e.g., agent proposes, human approves)
- **Hybrid** (agents for routine, human for critical decisions)

For each pattern, give me:
- Fit score (1-10) for my use case with reasoning
- Estimated complexity to implement
- Failure modes I should worry about
- Monthly API cost estimate

### 2. Agent Capability Matrix
Create a decision matrix mapping my project's tasks to agent capabilities:

| Task | Can Automate? | Confidence | Risk if Wrong | Recommended Pattern |
|------|--------------|------------|---------------|-------------------|
| [identify 5-8 key tasks from my project description] |

### 3. Guardrails Design
Based on my risk tolerance, design:
- **Pre-execution checks** — what the agent must verify before acting
- **Runtime boundaries** — hard limits on what agents can do
- **Post-execution validation** — how to verify agent output
- **Escalation triggers** — when to pull in a human

### 4. Implementation Roadmap
Give me a phased rollout plan:
- **Phase 1 (Week 1-2):** Start with [lowest risk task]
- **Phase 2 (Week 3-4):** Expand to [medium risk tasks]
- **Phase 3 (Month 2+):** Graduate to [higher autonomy]

Include specific tool/framework recommendations with version numbers.

### 5. Evaluation Metrics
Define how I'll measure if agents are actually helping:
- Task completion rate
- Error rate vs manual baseline
- Time saved per sprint
- Cost per automated task
- Developer satisfaction score

## Output Format
Structure your response with clear headers, tables where useful, and concrete examples using my actual project context. No generic advice — everything should reference my specific situation.
```

## When to Use This

- Starting a new project and considering AI agents
- Migrating from copilot-only to agent workflows
- Evaluating frameworks (CrewAI vs LangGraph vs custom)
- Building the business case for AI agent adoption
- After your team has outgrown basic AI autocomplete

## Example Use Case

A team building a SaaS platform wants to automate code review, deployment pipelines, and customer support ticket triage using AI agents. This prompt helps them evaluate whether to use a single orchestrator agent or specialized agents per domain.

## Pro Tips

- Be specific about your project — vague inputs get generic outputs
- Include your actual tech stack for framework-specific recommendations
- Run this prompt quarterly as the agent landscape evolves fast

---

> 🚀 **Want the complete Agent Toolkit?** This is 1 of 12+ agent prompts in the [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) — includes multi-agent orchestration templates, LangGraph workflow builders, agent testing frameworks, and production deployment configs. **$9 one-time.**
