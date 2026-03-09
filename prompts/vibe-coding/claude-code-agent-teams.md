# Claude Code Agent Teams — Starter Config

> 🔥 **Trending (March 2026):** Claude Code agent teams and subagents are the #1 topic in AI-assisted development. This template gets you started with parallel agent workflows.

## The Prompt

```markdown
You are a senior engineering lead setting up a Claude Code agent team for a project.

## Context
- Project: {{PROJECT_DESCRIPTION}}
- Stack: {{TECH_STACK}}
- Team size: {{TEAM_SIZE}} parallel agents

## Task
Generate a complete Claude Code agent team configuration including:

### 1. CLAUDE.md (Root — under 300 lines)
- One-line project description
- Code style (formatting, naming, imports)
- Architecture constraints (patterns to follow/avoid)
- Testing requirements
- Reference to AGENTS.md files in subdirectories

### 2. AGENTS.md Files (per module/feature area)
For each major area of the codebase, create an AGENTS.md with:
- Module purpose and boundaries
- Key dependencies and interfaces
- Domain-specific rules the agent MUST follow
- Common mistakes to avoid (what the agent gets wrong without this)
- Testing patterns specific to this module

### 3. Agent Team Roles
Define 3-5 specialized agent roles:

**🏗️ Architect Agent**
- Scope: System design, API contracts, database schemas
- Allowed: Create/modify interfaces, schemas, configs
- Forbidden: Implementation details, UI code

**⚡ Feature Agent (x{{TEAM_SIZE}})** 
- Scope: Implement features within defined boundaries
- Allowed: Code within assigned module, tests
- Forbidden: Cross-module changes, schema migrations

**🔍 Review Agent**
- Scope: Code review, security audit, test coverage
- Allowed: Read all, suggest changes
- Forbidden: Direct code modifications

**🧪 QA Agent**
- Scope: Integration tests, E2E tests, edge cases
- Allowed: Test files, fixtures, mocks
- Forbidden: Production code changes

### 4. Coordination Rules
```yaml
delegation:
  mode: parallel          # agents work simultaneously
  context_isolation: true # each agent gets only its AGENTS.md
  plan_approval: true     # architect approves before feature work
  quality_gate: review    # review agent checks before merge

task_assignment:
  strategy: module-based  # assign by directory ownership
  max_files_per_agent: 15 # prevent context overflow
  
conflict_resolution:
  interface_changes: architect-only
  shared_utils: lock-and-notify
  test_fixtures: copy-on-write
```

### 5. Example Workflow
Show a concrete example of how these agents would collaborate on a typical feature request, from ticket to merged PR.

## Output Format
- Provide each file separately with clear file paths
- Use real patterns from the specified tech stack
- Include inline comments explaining WHY each rule exists
- Keep CLAUDE.md under 300 lines, AGENTS.md under 100 lines each
```

## Example Output Structure

```
project/
├── CLAUDE.md                    # Root config (~250 lines)
├── AGENTS.md                    # Root agent coordination
├── src/
│   ├── api/
│   │   └── AGENTS.md           # API module rules
│   ├── core/
│   │   └── AGENTS.md           # Business logic rules
│   ├── db/
│   │   └── AGENTS.md           # Database module rules
│   └── ui/
│       └── AGENTS.md           # Frontend rules
└── .claude/
    └── team-config.yaml         # Agent team definitions
```

## Why This Works

- **Context isolation** prevents agents from stepping on each other
- **Module-scoped AGENTS.md** keeps each agent focused with minimal context
- **Plan approval** catches architectural mistakes before implementation
- **Quality gates** ensure consistency across parallel work

## Pro Tips

- Keep CLAUDE.md under 300 lines — everything else is a Skill or AGENTS.md
- Put "what Claude gets wrong" in AGENTS.md, not general docs
- Use subagents for parallelizable work, skills for repeatable workflows
- Monitor token costs per agent — bloated context = wasted money

---

> 💡 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes production-ready team configs for Next.js, FastAPI, Go microservices, and monorepo setups — plus 10+ pre-built agent role templates with battle-tested coordination patterns. **Just $9 USD.**
