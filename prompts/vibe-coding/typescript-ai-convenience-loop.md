# 🔄 TypeScript AI Convenience Loop Setup

TypeScript surged to #1 on GitHub because AI coding tools work dramatically better with static types. This prompt sets up your TypeScript project to maximize AI coding assistance — creating the "convenience loop" where types help the AI, and the AI helps you write better types.

## The Prompt

```
You are a TypeScript expert who optimizes projects for AI-assisted development. I want to set up my project so that AI coding tools (Cursor, Copilot, Claude Code) can be maximally effective.

My project:
- **Type:** {PROJECT_TYPE: e.g., Next.js app, API server, CLI tool, library}
- **Runtime:** {RUNTIME: Node.js | Bun | Deno}
- **Current state:** {STATE: new project | migrating from JS | existing TS project}

Set up the AI-optimized TypeScript convenience loop:

### 1. TypeScript Config for AI
Generate a `tsconfig.json` that maximizes type information for AI tools:
- Strict mode settings that help AI understand intent
- Path aliases that make imports readable
- Which strict flags matter most for AI assistance and why
- Recommended `include`/`exclude` patterns

### 2. Type Architecture
Design a type structure that gives AI maximum context:
- Where to put shared types (`types/`, co-located, or barrel exports?)
- Branded types for domain concepts (UserId, Email, etc.)
- Zod schemas that serve as BOTH runtime validation AND static types
- Discriminated unions for state machines and API responses
- Template literal types for route/event patterns

Show concrete examples for each pattern.

### 3. AI-Friendly Code Patterns
For each pattern, show before (AI struggles) and after (AI excels):
- Function signatures that give AI enough context to implement the body
- Error handling with typed errors (Result pattern or Effect)
- API client with fully typed requests/responses
- Database queries with type-safe results (Drizzle/Prisma)
- Event handlers with typed payloads

### 4. Documentation as AI Context
- JSDoc patterns that help AI tools (which tags matter?)
- `@example` annotations that serve as implicit tests
- Interface comments that guide AI implementation
- `@see` references that help AI find related code

### 5. Project Files for AI Tools
Generate these files optimized for AI coding:
- `AGENTS.md` — project context for Claude Code
- `.cursorrules` — coding standards for Cursor
- Type barrel files that give AI one-stop-shop imports

### 6. Validation & Testing Types
- Zod schemas → TypeScript types → test factories (one source of truth)
- Type-level tests with `expectTypeOf` patterns
- How to test that AI-generated code matches your type contracts

Output everything as files I can add to my project right now.
```

## Example Usage

```
Project: Next.js 15 SaaS with tRPC API, Drizzle ORM, Stripe billing
Runtime: Node.js
State: existing TS project, but types are loose and AI keeps hallucinating wrong APIs
```

## Tips

- The tighter your types, the better AI coding tools perform — this is the core loop.
- Zod + TypeScript inference = single source of truth for validation AND types.
- Branded types prevent AI from mixing up `userId` and `teamId` (a common AI mistake).
- Keep a `types/` barrel file — AI tools load it to understand your domain model.

---

> 🚀 **Get the full TypeScript + AI setup kit.** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes production-ready tsconfig templates, Zod schema patterns, AI-optimized project scaffolds, and type architecture guides for every major framework.
