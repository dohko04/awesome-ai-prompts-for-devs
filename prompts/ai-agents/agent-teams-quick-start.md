# 🤖 AI Agent Teams — Quick Start Guide

> **Trending (March 2026):** Both Claude Code and OpenAI Codex now support multi-agent workflows. This prompt helps you design your first agent team for any project.

## The Prompt

```markdown
You are a senior AI engineering lead designing an agent team for a software project.

## Project Context
- **Project:** {{PROJECT_DESCRIPTION}}
- **Tech stack:** {{TECH_STACK}}
- **Codebase size:** {{APPROX_FILES_AND_LOC}}
- **AI tool:** {{CLAUDE_CODE_OR_CODEX}}

## Task
Design a minimal but effective agent team with these outputs:

### 1. Team Structure (3-5 agents max)
For each agent define:
- **Role name** (e.g., "Backend Agent", "Test Agent")
- **Scope** — exactly which files/directories this agent owns
- **Rules** — 3-5 constraints this agent must follow
- **Dependencies** — which other agents it needs output from

### 2. Coordination Protocol
- How agents share context (shared files, handoff docs, git branches)
- Conflict resolution when two agents modify the same file
- Merge strategy (sequential vs parallel with review)

### 3. Root Configuration
Generate CLAUDE.md (for Claude Code) or equivalent config:
- Project conventions
- Architecture boundaries
- Testing requirements
- What agents should NEVER do
```

## Example: 3-Agent Team for a Next.js App

```
Agent 1: Frontend (app/, components/)
  - Must use server components by default
  - No client-side data fetching without approval

Agent 2: API (api/, lib/db/)
  - All endpoints must have Zod validation
  - Must write integration tests for each route

Agent 3: Quality (tests/, docs/)
  - Reviews all changes from Agent 1 & 2
  - Runs test suite, reports failures
  - Updates documentation
```

## Key Principles

1. **Clear boundaries** — Each agent owns specific directories
2. **Minimal overlap** — Shared files need explicit merge rules
3. **Quality gate** — Always have one agent that reviews others
4. **Start small** — 3 agents > 7 confused agents

---

> 🚀 **Need production-grade agent teams?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes complete agent team configurations for 8 project archetypes (monorepo, microservices, fullstack, mobile, data pipeline, etc.), advanced coordination patterns, error recovery protocols, and cost optimization strategies for running parallel agents efficiently.
