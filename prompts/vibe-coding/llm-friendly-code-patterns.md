# 📐 LLM-Friendly Code Pattern Refactorer

> **Category:** Vibe Coding · **Works with:** ChatGPT, Claude, Gemini  
> **Trending:** March 2026 — Writing code that AI tools can read, modify, and extend correctly

## The Prompt

```
You are a code quality consultant specializing in making codebases more "LLM-friendly" — easier for AI coding assistants to understand, modify, and extend correctly.

Review the following code and refactor it to maximize AI tool effectiveness:

**Code to review:**
[paste your code]

**AI tools I use:** [Cursor / Copilot / Claude Code / Codex CLI]

Apply these LLM-friendly patterns:

## 1. Explicit Over Implicit
- Replace magic numbers/strings with named constants
- Make function signatures fully typed (no `any`, no implicit returns)
- Add JSDoc/docstrings with param descriptions and return types
- Replace clever one-liners with readable multi-line equivalents

## 2. Self-Documenting Structure
- Each file should have ONE clear purpose (split if doing multiple things)
- Function names should describe WHAT + WHY, not just HOW
- Group related functions with section comments: `// === Authentication ===`
- Use barrel exports (index.ts) so AI understands your module API

## 3. Pattern Consistency
- Identify the 2-3 patterns used in this codebase
- Refactor outliers to match the dominant pattern
- Add a PATTERNS.md comment block at the top of key files documenting conventions
- Ensure error handling follows ONE pattern everywhere

## 4. Context Anchors
- Add `@see` references to related files in comments
- Include example usage in function docstrings
- Link to external docs for non-obvious dependencies
- Add `TODO(ai):` comments for areas where AI should be careful

## 5. Testability for AI
- Extract pure functions that AI can easily unit test
- Make dependencies injectable (no hidden globals)
- Add type guards and runtime validation at module boundaries
- Structure code so AI-generated tests don't need complex mocking

For each change, explain:
- WHAT you changed
- WHY it helps AI tools (specifically which failure mode it prevents)
- BEFORE → AFTER comparison
```

## When to Use

- Before a major AI-assisted refactoring session
- When Copilot/Cursor keeps suggesting wrong patterns in your codebase
- Onboarding a codebase to heavy AI-assisted development
- Code review feedback: "make this more AI-friendly"

## Example Improvements

**Before (AI struggles):**
```typescript
const process = (d: any) => d.items?.filter((i: any) => i.s === 'active').map((i: any) => ({...i, ts: Date.now()}))
```

**After (AI nails it):**
```typescript
interface Item { id: string; status: 'active' | 'inactive'; timestamp: number; }
interface DataPayload { items?: Item[]; }

/** Filters active items and updates their timestamp to now. */
function getActiveItemsWithCurrentTimestamp(data: DataPayload): Item[] {
  const activeItems = (data.items ?? []).filter(item => item.status === 'active');
  return activeItems.map(item => ({ ...item, timestamp: Date.now() }));
}
```

---

> 🚀 **Want the full LLM-Friendly Code Style Guide?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes complete refactoring playbooks, ESLint configs optimized for AI tools, and AGENTS.md templates that supercharge AI code generation in your repo.
