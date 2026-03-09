# 🤖 Codex CLI Agent Workflow Designer

> **Category:** Vibe Coding · **Works with:** OpenAI Codex CLI, Claude Code, Aider  
> **Trending:** March 2026 — CLI-based AI agents (Codex, Claude Code) are replacing IDE plugins for complex tasks

## The Prompt

```
You are an expert at designing workflows for CLI-based AI coding agents (OpenAI Codex CLI, Claude Code, Aider). These tools run in the terminal, can read/write files, run commands, and execute multi-step tasks autonomously.

I need a workflow for: [DESCRIBE YOUR TASK]

**My project:** [language, framework, repo structure]
**Agent I'm using:** [Codex CLI / Claude Code / Aider / other]
**Complexity:** [single file change / multi-file refactor / full feature / cross-repo]

Design a complete agent workflow:

## 1. Context Priming
Write the exact initial prompt I should give the agent, including:
- Project context it needs to know
- Files it should read first (be specific about paths)
- Constraints and coding standards to follow
- What SUCCESS looks like (acceptance criteria)

## 2. Task Decomposition
Break the work into sequential agent commands:
- Step 1: [what to ask the agent to do first]
- Step 2: [what depends on step 1's output]
- Step N: [final verification step]

For each step, specify:
- The exact prompt/instruction
- Which files will be modified
- How to verify the step succeeded before moving on

## 3. Guardrails
- What should the agent NEVER do? (e.g., never modify .env, never delete tests)
- File patterns to protect (glob patterns for agent config)
- Maximum scope per step (prevent runaway changes)

## 4. Verification Commands
After each step, what commands should run to validate:
- `npm test` / `pytest` / etc.
- Type checking: `tsc --noEmit` / `mypy`
- Lint: `eslint` / `ruff`
- Build: `npm run build`

## 5. Rollback Plan
If something goes wrong:
- Git checkpoint strategy (commit between steps?)
- How to identify which step broke things
- Recovery commands

Output the complete workflow as a numbered checklist I can follow.
```

## When to Use

- Planning complex multi-step coding tasks for AI agents
- Setting up repeatable workflows for common operations (migrations, refactors)
- Training your team on effective CLI agent usage
- When IDE-based AI isn't enough and you need terminal-level autonomy

## Example Tasks This Works Great For

- "Migrate all API routes from Express to Hono"
- "Add comprehensive error handling across 15 service files"
- "Convert JavaScript project to TypeScript incrementally"
- "Add OpenTelemetry instrumentation to all endpoints"

## Pro Tips

1. **Commit between steps** — Always `git add -A && git commit -m "checkpoint"` between agent steps. Cheap insurance.
2. **Scope is everything** — One focused task per agent call beats a vague mega-prompt every time
3. **Read-first prompts** — Start with "Read these 3 files and summarize the patterns" before asking for changes
4. **Test-driven agents** — Write the test first, then ask the agent to make it pass

---

> 🚀 **Want 15+ pre-built agent workflows?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes ready-to-run workflows for Codex CLI, Claude Code, and Aider — migration playbooks, refactoring pipelines, and multi-agent orchestration configs.
