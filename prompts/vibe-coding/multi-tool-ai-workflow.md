# 🔧 Multi-Tool AI Dev Workflow Setup

> 70% of engineers juggle 2-4 AI tools simultaneously. Stop context-switching blindly — set up a proper workflow where each tool handles what it's best at.

## The Prompt

```
You are an AI-assisted development workflow architect. Help me set up an efficient multi-tool workflow.

MY TOOLS: {{list your AI tools, e.g., Claude Code, Cursor, GitHub Copilot, ChatGPT}}
PROJECT TYPE: {{web app, API, CLI, mobile, data pipeline, etc.}}
LANGUAGE: {{primary language}}

Design a workflow that assigns each tool to what it does best:

1. **Tool Role Matrix** — For each tool:
   - Primary use case (what it's BEST at)
   - Secondary use case
   - What to NEVER use it for
   - Recommended model/config

2. **Workflow Phases** — Map tools to development phases:
   - Planning & Architecture → which tool?
   - Scaffolding & Boilerplate → which tool?
   - Feature Implementation → which tool?
   - Debugging & Fixing → which tool?
   - Code Review & Refactoring → which tool?
   - Testing → which tool?
   - Documentation → which tool?

3. **Context Sharing Strategy**
   - How to pass context between tools efficiently
   - Project files that help ALL tools (AGENTS.md, CLAUDE.md, .cursorrules)
   - What to put in each config file

4. **Quick Reference Card** — A cheat sheet I can pin:
   "For X, use Y with prompt Z"

Be opinionated. I want a clear workflow, not "it depends."
```

## Recommended 2026 Stack

Based on current benchmarks and community feedback:

| Phase | Best Tool | Why |
|-------|-----------|-----|
| Architecture | Claude (chat) | Best at reasoning about systems |
| Implementation | Claude Code / Cursor | Agentic coding with full codebase context |
| Quick edits | GitHub Copilot | Fastest inline completions |
| Debugging | Claude Code | Can read errors + fix in one loop |
| Code Review | Codex | Async background review |
| Docs | Any chatbot | All roughly equal here |

## The Golden Rule

**One tool per task, not one tool for everything.** The devs getting 2-3x productivity gains aren't using one magic tool — they're routing the right task to the right tool.

---

> 💡 **Get the complete workflow configs.** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) includes ready-to-use config files (.cursorrules, CLAUDE.md, .github/copilot-config) pre-tuned for 8 different project types — plus a CLI tool that generates them automatically.
