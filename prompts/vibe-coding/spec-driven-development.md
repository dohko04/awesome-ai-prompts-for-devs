# Spec-Driven AI Development — Stop Vibe Coding, Start Spec Coding

> 🔥 **Trending (March 2026):** AWS Kiro popularized spec-driven development where AI agents follow structured specs instead of freeform prompts. Engineers report 3x fewer revision cycles compared to pure vibe coding. This prompt brings that discipline to any AI agent.

## The Prompt

```markdown
You are a spec-driven development expert. Help me write a structured specification that any AI coding agent (Claude Code, Cursor, Copilot, Kiro) can follow to implement a feature correctly on the first try.

## My Feature
- **What it does:** [describe the feature]
- **Tech stack:** [e.g., Next.js 15, TypeScript, Prisma]
- **Existing codebase patterns:** [paste a sample file or describe conventions]

## Generate a Complete Spec:

### 1. Feature Spec (SPEC.md)
```markdown
# Feature: [Name]

## User Story
As a [role], I want [action] so that [outcome].

## Acceptance Criteria
- [ ] Given [context], when [action], then [result]
- [ ] Given [context], when [action], then [result]
- [ ] Edge case: [scenario] → [expected behavior]

## Technical Constraints
- Must use existing [pattern/library]
- Performance: [latency/memory budget]
- Security: [auth requirements]
```

### 2. Implementation Plan (PLAN.md)
Break the feature into ordered tasks that an AI agent can execute sequentially:
1. **Task 1:** Create [file] with [purpose] — estimated ~[N] lines
2. **Task 2:** Modify [existing file] to [change] — touch only [specific function]
3. **Task 3:** Add tests for [scenarios]

### 3. Context Package
List exactly which files the AI agent needs to read before starting:
- `src/types/...` — for type definitions
- `src/lib/...` — for shared utilities
- `tests/...` — for testing patterns

### 4. Validation Checklist
After implementation, verify:
- [ ] All acceptance criteria pass
- [ ] No existing tests broken
- [ ] Types compile with no errors
- [ ] Follows existing code conventions

### 5. Agent-Specific Instructions
Generate the exact prompt I should paste into my AI agent to start implementation, referencing the spec.
```

## Why This Works

Pure vibe coding produces inconsistent results on complex features. Spec-driven development gives AI agents the guardrails they need — clear acceptance criteria, explicit file boundaries, and ordered tasks. It's the difference between "build me a login page" and a junior dev's first-day onboarding doc.

> 💡 **Want the full version?** The complete prompt includes spec templates for 12 common feature types (CRUD, auth, payments, real-time, etc.), auto-validation scripts, and a chained workflow that generates specs → implementation → tests in sequence.
>
> 👉 **[Get the AI Dev Toolkit — 55+ pro prompts for $9](https://ai-dev-toolkit-five.vercel.app)** — Pay with ETH, instant access.

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) · Built by [Dohko](https://github.com/dohko04)*
