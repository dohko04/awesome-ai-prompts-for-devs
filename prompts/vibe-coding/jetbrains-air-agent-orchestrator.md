# JetBrains Air — Multi-Agent Orchestration Starter

> Set up parallel AI agent workflows in JetBrains Air (Public Preview, March 2026). Run Codex, Claude Agent, Gemini CLI, and Junie simultaneously on the same codebase.

## The Prompt

```markdown
You are an expert at configuring JetBrains Air agentic development environments.

I'm setting up JetBrains Air for my project. Help me create an optimal multi-agent orchestration configuration.

## Project Context
- **Language/Framework:** [e.g., TypeScript/Next.js, Python/FastAPI, Rust]
- **Repo size:** [small/medium/large monorepo]
- **Team size:** [solo/small team/large team]

## What I Need

### 1. Agent Assignment Strategy
For each type of task, recommend which agent to assign:
- **Feature implementation:** [Codex / Claude Agent / Junie]
- **Bug investigation:** [best agent for debugging]
- **Test generation:** [best agent for test coverage]
- **Refactoring:** [best agent for safe refactors]
- **Documentation:** [best agent for docs]

### 2. Context Scoping Template
For each task delegation, I need precise context. Give me a template:
```
Task: [description]
Scope: [file, class, method, commit range]
Constraints: [don't touch X, preserve Y interface]
Output: [PR-ready diff / investigation report / test file]
```

### 3. Sandboxing Rules
- When should I use Docker isolation vs Git worktrees?
- Which agents need sandboxing for my project type?

### 4. Parallel Workflow Design
Design a workflow where 3 agents work simultaneously:
- Agent A: implements feature
- Agent B: writes tests for the feature spec
- Agent C: updates documentation
Show how to coordinate without conflicts.

## Output Format
Give me:
1. A concrete agent assignment table for my stack
2. 3 ready-to-use task delegation templates
3. Sandboxing recommendations
4. A parallel workflow example I can use today
```

## Example Output (Abbreviated)

| Task Type | Recommended Agent | Why |
|-----------|------------------|-----|
| Feature impl | Claude Agent | Best at complex multi-file changes |
| Test generation | Codex | Fast, accurate unit test generation |
| Refactoring | Junie | JetBrains-native, understands project structure |
| Bug investigation | Gemini CLI | Strong reasoning on large context |

### Task Delegation Template
```
Task: Add user authentication middleware
Scope: src/middleware/auth.ts, src/routes/api/*
Constraints: Must use existing JWT library, don't modify User model
Output: PR-ready diff with inline comments explaining decisions
```

## Tips

- **Start with 2 agents max** — adding more increases coordination overhead
- **Use Git worktrees** for feature work, Docker for untrusted/experimental agents
- **Check Air's notification system** — it tells you when an agent needs your input
- **Assign clear boundaries** — overlapping file scopes cause merge conflicts

## When to Use This

- You just got JetBrains Air access (Public Preview)
- You want to parallelize coding tasks across multiple AI agents
- You're evaluating which agent works best for your stack
- You want to reduce context-switching between different AI coding tools

---

> ⚡ **Want the complete JetBrains Air production setup?** The [AI Dev Toolkit ($9)](https://survive-ochre.vercel.app) includes agent routing matrices, cost optimization per agent, conflict resolution patterns, and a full multi-agent CI/CD integration guide.
