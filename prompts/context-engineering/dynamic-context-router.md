# 🧩 Dynamic Context Router

> Not every task needs the same context. This prompt helps you build a routing system that dynamically selects and prioritizes context based on what the AI is actually trying to do.

## The Prompt

```
You are a Dynamic Context Router. Design a context routing strategy that automatically selects the right context for different types of AI tasks in a development workflow.

## Project Setup
- Stack: {{STACK}}
- AI Tools: {{TOOLS}} (e.g., Claude Code, Cursor, Copilot)
- Team size: {{TEAM_SIZE}}
- Repo size: {{REPO_SIZE}} (files/LOC estimate)

## Task Categories to Route

For each task type, define the optimal context configuration:

### 🐛 Bug Fix
**Context priority:**
1. Error logs / stack trace (CRITICAL)
2. Failing test or reproduction steps
3. Source file + immediate dependencies
4. Recent git changes to affected files
5. Related issue/ticket description

**Context budget:** ~40% of window
**Strategy:** Narrow and deep — few files, full context

### ✨ New Feature  
**Context priority:**
1. Feature spec / ticket description (CRITICAL)
2. Similar existing features (pattern reference)
3. Relevant type definitions & interfaces
4. Database schema (affected tables)
5. API contracts (new/modified endpoints)
6. Test patterns to follow

**Context budget:** ~60% of window
**Strategy:** Broad but structured — many files, key sections only

### ♻️ Refactor
**Context priority:**
1. Files to refactor (full content) (CRITICAL)
2. All callers/consumers of the code
3. Test coverage for affected code
4. Target architecture / design pattern
5. Style guide & conventions

**Context budget:** ~70% of window  
**Strategy:** Complete picture — need to see all dependencies

### 📝 Code Review
**Context priority:**
1. PR diff (CRITICAL)
2. Full files for changed sections
3. Project conventions / AGENTS.md
4. Security checklist
5. Performance guidelines

**Context budget:** ~50% of window
**Strategy:** Diff-centric with surrounding context

### 🧪 Test Writing
**Context priority:**
1. Source code to test (CRITICAL)
2. Existing test examples (pattern reference)
3. Test framework setup / helpers
4. Mock/fixture patterns
5. Edge cases from requirements

**Context budget:** ~50% of window
**Strategy:** Source + examples — heavy on patterns

## Generate Router Config

Output a decision tree or routing table:

| Signal | Task Type | Context Sources | Token Budget |
|--------|-----------|-----------------|-------------|
| Error in logs | Bug Fix | logs, source, deps, git blame | 40% |
| "Add/create/implement" | New Feature | spec, patterns, types, schema | 60% |
| "Refactor/clean/modernize" | Refactor | source, callers, tests | 70% |
| PR/diff provided | Code Review | diff, files, conventions | 50% |
| "Test/spec/coverage" | Test Writing | source, test examples, fixtures | 50% |

## Implementation Notes
- How to detect task type automatically
- How to gather context sources (CLI commands, file globs, git commands)  
- How to compress when context exceeds budget
- How to validate context quality before sending to LLM
```

## When to Use

- Building custom AI coding workflows or IDE extensions
- Setting up team-wide AI development standards
- Designing the context layer for AI agents
- Optimizing token usage across different task types

---

> 🎯 **The Full Toolkit** includes production-ready context routers, automatic task detection, and pre-built configurations for every major AI coding tool.  
> [**Get it → $9 one-time**](https://ai-dev-toolkit-five.vercel.app)
