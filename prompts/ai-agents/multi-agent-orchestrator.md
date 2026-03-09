# Multi-Agent Orchestrator — Coordinate AI Agents Like a Senior Tech Lead

> 🔥 **Trending (March 2026):** 55% of engineers now regularly use AI agents (not just autocomplete). The Pragmatic Engineer survey shows devs run 2-4 AI tools simultaneously. This prompt helps you orchestrate them without chaos.

## The Prompt

```markdown
You are an expert AI agent orchestration architect. Help me design a multi-agent workflow where different AI agents handle different parts of my development pipeline.

## My Setup
- **Project:** [describe your project]
- **Agents available:** [e.g., Claude Code, Cursor, Copilot, Codex]
- **Team size:** [solo / small team / large team]

## Design a Multi-Agent Pipeline:

### 1. Agent Role Assignment
For each agent I have, define:
- **Primary role** (e.g., Claude Code → architecture & complex logic, Cursor → UI iteration, Copilot → inline completions)
- **Handoff protocol** — how work passes between agents
- **Context boundaries** — what each agent should/shouldn't see

### 2. Orchestration Rules
Create a `.agents-config.md` file that defines:
- Which agent handles which file types/directories
- Conflict resolution when agents disagree
- Review gates (human checkpoints)
- Shared context files all agents can read

### 3. Workflow Stages
Map my development cycle to agents:
1. **Planning** → Which agent writes specs?
2. **Implementation** → Which agent writes code?
3. **Review** → Which agent reviews the other's code?
4. **Testing** → Which agent writes/runs tests?
5. **Deployment** → Which agent handles CI/CD?

### 4. Anti-Collision Patterns
- File locking conventions
- Branch-per-agent strategies
- Merge conflict prevention
- Context window budget allocation

### 5. Monitoring Dashboard
Give me a checklist to track agent performance:
- Lines of code accepted vs rejected per agent
- Time-to-merge per agent
- Hallucination rate by task type
```

## Why This Works

The era of "one AI tool" is over. Top engineers now use Claude Code for complex reasoning, Cursor for rapid UI iteration, and Copilot for inline flow — all on the same project. Without orchestration, they step on each other. This prompt gives you the playbook.

> 💡 **Want the full version?** The complete prompt includes pre-built orchestration configs for 6 popular agent combinations, a ready-to-use `.agents-config.md` template, and a performance tracking spreadsheet.
>
> 👉 **[Get the AI Dev Toolkit — 55+ pro prompts for $9](https://ai-dev-toolkit-five.vercel.app)** — Pay with ETH, instant access.

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) · Built by [Dohko](https://github.com/dohko04)*
