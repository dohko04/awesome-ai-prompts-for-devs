# 🌙 Night Shift Agentic Workflow Setup

> Based on the viral "Night Shift" pattern (March 2026) — humans spec during the day, agents implement overnight autonomously. 5x faster, better quality, no babysitting.

## The Prompt

```
You are an AI workflow architect specializing in the "Night Shift" agentic pattern — 
where human developers write specs during the day and AI agents implement them 
autonomously overnight.

Given my project context:
- Project type: [web app / mobile / CLI / library / API]
- Tech stack: [e.g., TypeScript, React, Node.js, Python]
- Current team size: [solo / 2-5 / 5+]
- AI tools available: [Claude Code / Cursor / Copilot / Codex CLI]

Design my Night Shift workflow:

## 1. Day Shift (Human Phase)
Create a SPEC_TEMPLATE.md I'll use to write feature specs that include:
- Feature description and acceptance criteria
- Edge cases to cover
- Testing requirements
- Relevant existing code paths
- Architecture constraints

## 2. AGENT_LOOP.md
Create the agent instruction file that will:
- Clean working tree (stash/commit uncommitted work)
- Run existing test suite, fix any failures
- Pick tasks from ./Specs/ (bugs first, then features, skip draft-*)
- For each spec: analyze → load docs → write tests → implement → review → commit
- Use sub-agent review personas (Architect, Domain Expert, Code Expert)
- Create a morning report in ./Reports/

## 3. AGENTS.md Router
Create a small (~150 line) router file that tells agents where to find:
- Workflow documentation
- Skill/capability docs
- System architecture docs
- Coding standards

## 4. Morning Review Checklist
What I should check each morning in <15 minutes to accept/reject night work.

Keep everything practical and immediately usable.
```

## What You Get

- Spec template for structured handoff to agents
- Agent loop instruction file for autonomous overnight work
- Router file pointing agents to your documentation
- Morning review checklist for quick quality assessment

## Example Output

The agent will generate a complete workflow setup including:
- `SPEC_TEMPLATE.md` with structured sections
- `AGENT_LOOP.md` with step-by-step autonomous instructions
- `AGENTS.md` router for documentation discovery
- Morning review checklist (~15 min daily)

## Why This Works

The Night Shift pattern solves the biggest problems with AI coding:
- **No babysitting** — agents work while you sleep
- **You stay in control** — specs are YOUR architecture decisions
- **Quality stays high** — sub-agent reviewers catch issues
- **5x throughput** — your day is for thinking, nights are for building

---

## 🚀 Want the Full Production Pipeline?

The **[AI Developer Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes the complete **Night Shift Production Pipeline PRO** with:
- ✅ 6 review persona configurations (Architect, Designer, Domain Expert, Code Expert, Performance Expert, Human Advocate)
- ✅ Multi-agent orchestration configs for Claude Code, Cursor, and Codex CLI
- ✅ Automated morning report generator with diff summaries
- ✅ Cost tracking & token budget calculator
- ✅ Team rollout playbook (solo → team adoption)
- ✅ CI/CD integration for overnight agent commits

**188+ production-ready resources for AI-powered development.**
