# Agent Teams Task Decomposer

> 🔥 **Trending (March 2026):** Claude Code Agent Teams shipped in Feb 2026 and multi-agent coordination is *the* pattern for tackling large codebases. This prompt helps you decompose any task into parallelizable sub-tasks for agent teams.

## The Prompt

```markdown
You are an expert at parallel task decomposition for AI coding agent teams (Claude Code Agent Teams, Cursor background agents, or similar multi-agent systems).

## Context
- Task: {{TASK_DESCRIPTION}}
- Codebase: {{CODEBASE_DESCRIPTION}} (monorepo? microservices? single app?)
- Stack: {{TECH_STACK}}
- Files likely involved: {{KEY_FILES_OR_DIRS}}
- Max parallel agents: {{MAX_AGENTS}} (default: 5)
- Time constraint: {{TIME_CONSTRAINT}} (e.g., "ship today", "this sprint")

## Task
Decompose my task into the optimal set of parallel sub-tasks for an agent team.

### 1. Dependency Graph
- Map which parts of the task depend on others
- Identify the critical path (longest sequential chain)
- Find tasks that can run 100% in parallel (no shared files)
- Flag potential merge conflicts (agents touching the same files)

### 2. Agent Assignments
For each sub-task, define:
- **Agent role**: (e.g., "backend-api", "frontend-ui", "test-writer", "docs")
- **Scope**: Exact files/directories this agent owns
- **Instructions**: What this specific agent should do (be precise)
- **Inputs**: What it needs from other agents before starting
- **Outputs**: What it produces that others depend on
- **Verification**: How to check this agent's work is correct

### 3. Orchestration Plan
Generate a concrete execution plan:
```
Phase 1 (parallel): [Agent A: task], [Agent B: task], [Agent C: task]
Phase 2 (parallel, after Phase 1): [Agent D: task], [Agent E: task]
Phase 3 (sequential): [Integration + testing]
```

### 4. AGENTS.md Files
For each agent, generate the AGENTS.md scoped instructions file that should be placed in its working directory. Include:
- Module boundaries (what it CAN and CANNOT touch)
- Code style specific to that module
- Known pitfalls in that area of the codebase
- Integration points with other agents' work

### 5. Integration Strategy
- How to merge all agents' work without conflicts
- Integration test suite to run after merge
- Rollback plan if an agent's output breaks things

## Output Format
- Mermaid diagram of the dependency graph
- Table of agent assignments
- Ready-to-use AGENTS.md files for each agent
- Shell commands to launch the agent team (Claude Code syntax)

## Constraints
- No agent should have a scope larger than 20 files
- Each agent must be able to verify its own work (tests must pass independently)
- Total estimated time should be <{{TIME_CONSTRAINT}}
- Prefer more smaller agents over fewer large ones (better parallelism)
```

## When to Use

- You have a large feature (50+ files) and want to ship it fast with parallel agents
- You're refactoring a monolith and need to coordinate changes across modules
- Your sprint has a complex task that one agent would take hours on
- You want to try Claude Code Agent Teams but aren't sure how to structure the work

## Pro Tips

1. **Start with 3 agents, not 10** — coordination overhead grows quadratically
2. **Give each agent its own test command** — `npm test --scope=backend` not just `npm test`
3. **Use file-level boundaries** — "you own `/src/api/**`" is clearer than "you handle API stuff"
4. **Always have an integration agent** — one agent whose only job is merging and running full tests

## Example: "Add Stripe billing to SaaS app"

```
Phase 1 (parallel):
  - Agent 1 (backend): Stripe API integration, webhook handlers
  - Agent 2 (database): Billing schema, migrations, models
  - Agent 3 (frontend): Pricing page, checkout flow UI

Phase 2 (parallel, needs Phase 1):
  - Agent 4 (integration): Wire backend↔frontend, test E2E
  - Agent 5 (docs): API docs, billing FAQ, changelog

Total: ~30 min with 5 agents vs ~2.5 hours with 1
```

---

> 💡 **Want agent team templates for 15+ common tasks?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes pre-built decomposition templates for migrations, refactors, new features, and more — plus orchestration scripts and 100+ engineering prompts for $9.
