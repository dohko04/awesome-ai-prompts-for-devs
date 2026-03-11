# Claude Cowork — Workflow Builder

> Design production workflows using Claude Cowork's plugins, sub-agents, scheduled tasks, and memory patterns. Covers both standalone Claude Cowork and Microsoft Copilot Cowork integration (March 2026).

## The Prompt

```markdown
You are a Claude Cowork power user and workflow architect.

I want to build an automated workflow using Claude Cowork's agentic capabilities. Help me design it end-to-end.

## My Use Case
- **What I want automated:** [e.g., daily code review digest, research pipeline, content generation]
- **Tools I use:** [e.g., GitHub, Slack, Notion, Linear, Jira]
- **Frequency:** [on-demand / scheduled / event-triggered]

## Design My Workflow

### 1. Plugin Selection
Which Cowork plugins should I connect for this workflow?
- List the essential plugins
- Explain what each one handles
- Note any plugin interactions or dependencies

### 2. Sub-Agent Architecture
Break my workflow into sub-agents:
- **Agent 1:** [role and responsibility]
- **Agent 2:** [role and responsibility]
- **Coordinator:** how they pass context between each other

### 3. Memory Strategy
- What should persist between sessions? (key context, preferences, decisions)
- What's ephemeral? (intermediate results, temp data)
- How to structure memory for reliable recall

### 4. Scheduled Tasks
- What runs on a schedule vs on-demand?
- Cron-like timing recommendations
- Error handling: what happens when a scheduled task fails?

### 5. Safety & Guardrails
- What actions need human approval before executing?
- Rate limits and cost controls
- Sensitive data handling

## Output Format
Give me:
1. A workflow diagram (text-based)
2. Plugin configuration list
3. 2 sub-agent definitions with clear boundaries
4. Memory schema
5. A sample scheduled task definition
```

## Example Output (Abbreviated)

### Workflow: Daily PR Review Digest

```
┌─────────────┐    ┌──────────────┐    ┌─────────────┐
│ GitHub       │───>│ Review Agent │───>│ Slack        │
│ Plugin       │    │ (Sub-agent)  │    │ Plugin       │
└─────────────┘    └──────────────┘    └─────────────┘
       │                   │
       │            ┌──────┴──────┐
       └───────────>│ Memory      │
                    │ (patterns)  │
                    └─────────────┘
```

**Plugins needed:** GitHub, Slack, Memory (built-in)
**Schedule:** Daily at 9 AM, skip weekends
**Human approval:** Required for auto-commenting on PRs

### Memory Schema
```json
{
  "teamPreferences": {
    "reviewStyle": "concise",
    "focusAreas": ["security", "performance"],
    "ignorePatterns": ["*.test.ts", "docs/*"]
  },
  "prHistory": {
    "lastReviewed": "2026-03-10",
    "recurringIssues": ["missing error handling", "no input validation"]
  }
}
```

## Key Patterns

- **Standalone Claude Cowork** — best for dev-centric workflows (code, CLI, APIs)
- **Copilot Cowork (M365)** — best for business workflows (docs, email, meetings)
- **Don't over-automate** — start with 1 workflow, validate, then expand
- **Memory is your secret weapon** — structured memory beats longer prompts

## When to Use This

- You want to build real automation with Claude Cowork (not just chat)
- You're comparing standalone Cowork vs Microsoft Copilot Cowork
- You need sub-agents that coordinate on complex tasks
- You want scheduled, recurring AI workflows

---

> ⚡ **Want 15+ production-ready Cowork workflow templates?** The [AI Dev Toolkit ($9)](https://survive-ochre.vercel.app) includes enterprise Cowork patterns, multi-agent coordination blueprints, memory optimization guides, and cost-tracking dashboards for agentic workflows.
