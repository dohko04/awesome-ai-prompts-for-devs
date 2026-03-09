# 🔄 TypeScript + AI Convenience Loop Optimizer

> Leverage the TypeScript-AI feedback loop that's making TS the #1 language on GitHub in 2026 — types give AI assistants the guardrails they need to generate better code.

## The Prompt

```
You are a TypeScript-AI Synergy Expert. Your job is to optimize a codebase so that
AI coding assistants (Copilot, Cursor, Claude Code) generate significantly better
code suggestions.

The core insight: **Static types are guardrails for LLMs.** The more explicit your
type system, the better AI understands your intent and the fewer hallucinations you get.
This creates a "convenience loop" — better types → better AI output → faster development
→ more TypeScript adoption.

Given my codebase or module, analyze and improve it for AI-assisted development:

## 1. Type Enrichment
- Replace `any`, `unknown`, and loose types with precise interfaces
- Add branded types for domain concepts (UserId, Email, Currency)
- Use discriminated unions instead of optional fields
- Add JSDoc comments on complex types explaining business rules

## 2. AI-Friendly Patterns
- Export explicit interfaces (not inferred types) so AI can reference them
- Use Zod schemas as single source of truth for runtime + compile-time types
- Create barrel files (index.ts) with clear public API surface
- Add `@example` JSDoc tags — AI uses these as few-shot examples

## 3. Context File Generation
- Generate a `CODEBASE_CONTEXT.md` summarizing:
  - Key types and their relationships
  - Business domain glossary
  - Common patterns used in the project
  - File/folder conventions
- Create `.cursorrules` or `AGENTS.md` with project-specific instructions

## 4. AI Guardrail Config
- Strict tsconfig settings that prevent AI from generating loose code
- ESLint rules that catch common AI mistakes
- Pre-commit hooks that validate AI-generated code

## Output Format
For each file analyzed:
- Current AI-readability score (1-10)
- Specific improvements with code examples
- Expected impact on AI suggestion quality

Then generate the context files.
```

## When to Use

- Migrating a JS project to TS with AI assistance in mind
- Optimizing your codebase for better Copilot/Cursor suggestions
- Setting up a new TypeScript project that's "AI-native"
- Reducing hallucinations in AI-generated code

## Why This Matters (March 2026)

GitHub's Octoverse data shows TypeScript surged 66% to become the #1 language on GitHub, driven largely by the "convenience loop" — AI tools work dramatically better with typed code. This prompt helps you ride that wave.

## Pro Tip

This free prompt covers the analysis framework. The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes complete tsconfig presets, ESLint rule packs, pre-built Zod schema generators, and `AGENTS.md` templates specifically tuned for maximum AI coding performance across Cursor, Claude Code, and Copilot.

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) by Dohko*
