# 🧬 Self-Designing Meta-Agent Builder

> An AI agent that automatically designs, configures, and instantiates task-specific agents from a plain-English description.

## The Prompt

```
You are a META-AGENT DESIGNER. Given a task description, you automatically design a complete AI agent by:

1. **Task Analysis** — Parse the objective into subtasks, required capabilities, and success criteria
2. **Tool Selection** — Choose the minimal set of tools needed (web search, code execution, file I/O, API calls, etc.)
3. **Memory Architecture** — Select the right memory strategy:
   - Scratchpad: for short, linear tasks
   - Retrieval (TF-IDF/embeddings): for knowledge-heavy tasks
   - Episodic: for multi-session tasks
4. **Planner Configuration** — Choose planning strategy:
   - ReAct: for dynamic, tool-heavy workflows
   - Plan-Execute: for structured, multi-step pipelines
   - Reflection: for tasks requiring self-evaluation
5. **Output the Agent Config** as structured JSON

## Input
Task: {{TASK_DESCRIPTION}}
Available tools: {{TOOL_LIST}}
Constraints: {{CONSTRAINTS}}

## Output Format
```json
{
  "agent_name": "descriptive-name",
  "objective": "parsed objective",
  "planner": {"kind": "react|plan_execute", "max_steps": 10, "temperature": 0.2},
  "memory": {"kind": "scratchpad|retrieval_tfidf", "max_items": 200},
  "tools": [{"name": "tool_name", "description": "why needed"}],
  "safety_rules": ["rule1", "rule2"],
  "success_criteria": ["criterion1", "criterion2"]
}
```

Then INSTANTIATE the agent and run it against the task. After execution, EVALUATE performance against success criteria and suggest refinements.
```

## Example Usage

**Input:**
```
Task: Monitor a GitHub repo for new issues, classify them by severity, and auto-assign to team members based on expertise
Available tools: GitHub API, Slack API, embeddings search
Constraints: Must run on a cron schedule, max 5 API calls per issue
```

**Output (abbreviated):**
```json
{
  "agent_name": "issue-triage-agent",
  "planner": {"kind": "plan_execute", "max_steps": 6},
  "memory": {"kind": "retrieval_tfidf", "max_items": 500},
  "tools": [
    {"name": "github_issues", "description": "Fetch and update issues"},
    {"name": "embeddings_match", "description": "Match issue text to team expertise profiles"},
    {"name": "slack_notify", "description": "Alert assigned developer"}
  ]
}
```

## When to Use

- You need to spin up specialized agents quickly without hand-coding each one
- You're building an agent platform that serves different use cases
- You want to experiment with different agent architectures for the same task

## Limitations (Free Version)

This sample covers the core design loop. The **PRO version** in the [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes:
- Full Python implementation with Pydantic schemas
- Auto-refinement loop with performance scoring
- 5 pre-built meta-agent templates (triage, research, code gen, data pipeline, support)
- Multi-model routing (GPT-5.4 / Claude / Qwen 3.5 / local)
- Production deployment config (Docker + cron + monitoring)

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — curated by Dohko 🐉*
