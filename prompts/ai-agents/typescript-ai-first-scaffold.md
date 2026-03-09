# 🏗️ TypeScript AI-First Project Scaffold

> TypeScript is the #1 language for AI-assisted development in 2026. Types give LLMs guardrails. This prompt scaffolds a project optimized for AI coding tools from day one.

## The Prompt

```
Create a TypeScript project scaffold optimized for AI-assisted development.

Project type: <API / CLI / Full-stack / Library>
Framework: <Express / NestJS / Fastify / Hono / None>
Purpose: <what it does>

Generate the complete scaffold with these AI-optimization principles:

1. **Strict TypeScript config** — `strict: true`, no `any`, explicit return types.
   AI tools generate better code when types constrain the output.

2. **Barrel exports with JSDoc** — Each module has an index.ts. Every exported
   function/class has JSDoc with @param, @returns, @throws, @example.
   AI reads these to understand intent.

3. **Zod schemas as source of truth** — Define schemas once, infer types with
   `z.infer<>`. AI tools use schemas to validate their own output.

4. **Error types, not strings** — Typed error classes extending AppError.
   `throw new NotFoundError("User", userId)` not `throw new Error("not found")`.

5. **Config as typed object** — Single `config.ts` with Zod-validated env vars.
   Never `process.env.X` scattered around.

6. **Repository pattern** — Even for simple projects. AI tools handle
   interface→implementation patterns better than ad-hoc DB calls.

7. **Test structure mirrors source** — `src/users/users.service.ts` →
   `tests/users/users.service.test.ts`. AI finds tests instantly.

8. **AI-ready scripts in package.json:**
   - `typecheck` — tsc --noEmit
   - `test` — with coverage
   - `lint:fix` — auto-fixable
   - `validate` — runs all three in sequence

9. **AGENTS.md included** — Pre-populated with the project conventions.

10. **.cursorrules included** — So Cursor follows the same patterns.

Output the file tree, then each file's content. Make it `npx degit`-ready.
```

## Why AI-First Matters

```
Without types:     AI guesses → 40% accuracy → you fix everything
With strict TS:    AI reads types → 85% accuracy → you review and ship
With Zod schemas:  AI validates → 95% accuracy → you approve and deploy
```

GitHub's 2025 Octoverse data confirms it: TypeScript surged 66% because AI tools
produce dramatically better code when types exist. This isn't preference — it's
a measurable productivity multiplier.

## Key Files to Include

```
├── src/
│   ├── config.ts              # Zod-validated env config
│   ├── errors.ts              # Typed error hierarchy
│   ├── app.ts                 # App setup
│   └── modules/
│       └── example/
│           ├── example.schema.ts      # Zod schemas
│           ├── example.types.ts       # Inferred types
│           ├── example.repository.ts  # Data access
│           ├── example.service.ts     # Business logic
│           ├── example.controller.ts  # HTTP handlers
│           └── index.ts              # Barrel export
├── tests/
├── AGENTS.md
├── .cursorrules
├── tsconfig.json              # strict: true
└── package.json               # AI-ready scripts
```

## 🐉 Want More?

This is a free sample from [**Dohko's AI Dev Toolkit**](https://ai-dev-toolkit-five.vercel.app). The full toolkit includes complete scaffolds for NestJS, Next.js, FastAPI, and Go — all AI-optimized with AGENTS.md, .cursorrules, and Zod/Pydantic schemas pre-configured.

[**Get the Full Toolkit → $9**](https://ai-dev-toolkit-five.vercel.app)
