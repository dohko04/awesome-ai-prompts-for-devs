# 🤖 AGENTS.md Generator for Claude Code

> Generate a perfect AGENTS.md file so Claude Code understands your codebase instantly. The #1 productivity hack for vibe coding in 2026.

## The Prompt

```
Analyze this project and generate an AGENTS.md file for Claude Code.

Project structure:
<paste your `find . -type f -not -path './.git/*' | head -80` output here>

Package.json / requirements.txt / go.mod (paste relevant):
<paste here>

Generate an AGENTS.md that includes:

1. **Project Overview** — What this project does in 2 sentences
2. **Tech Stack** — Languages, frameworks, key dependencies
3. **Architecture** — How the code is organized (folders, layers, patterns)
4. **Key Commands** — How to build, test, lint, deploy
5. **Code Conventions** — Naming, file structure, import order, patterns used
6. **Testing** — How tests are structured, how to run them, what framework
7. **Common Patterns** — Recurring patterns Claude should follow (error handling, logging, auth, etc.)
8. **Don'ts** — Things Claude should NEVER do in this codebase
9. **Database** — ORM, migrations, schema location (if applicable)
10. **Environment** — Required env vars, config files

Format it as a clean markdown file. Be specific to THIS project, not generic.
Every instruction should help an AI agent make correct changes on the first try.
```

## Example Output

```markdown
# AGENTS.md

## Project
E-commerce API built with NestJS + Prisma + PostgreSQL.

## Tech Stack
- TypeScript 5.4, NestJS 10, Prisma 5
- PostgreSQL 16, Redis 7 (caching)
- Jest for testing, ESLint + Prettier

## Architecture
src/
  modules/       # Feature modules (users/, orders/, products/)
  common/        # Shared decorators, guards, pipes, filters
  config/        # Configuration module with validation
  prisma/        # Prisma service and migrations

Each module follows: controller → service → repository pattern.

## Commands
- `pnpm dev` — Start dev server (port 3000)
- `pnpm test` — Run Jest tests
- `pnpm test:e2e` — E2E tests against test DB
- `pnpm prisma:migrate` — Run migrations
- `pnpm lint` — ESLint check

## Conventions
- Files: kebab-case (user-profile.service.ts)
- Classes: PascalCase, Interfaces prefixed with I (IUserResponse)
- All endpoints return { data, meta } wrapper
- Use ConfigService for env vars, never process.env directly
- Every service method has JSDoc with @throws

## Don'ts
- NEVER use raw SQL — always Prisma
- NEVER skip input validation (use class-validator DTOs)
- NEVER return Prisma models directly — map to response DTOs
- NEVER commit .env files
```

## Why This Works

Claude Code reads AGENTS.md before making any changes. A good one means:
- ✅ Follows YOUR patterns, not generic ones
- ✅ Uses the right commands and tools
- ✅ Respects your architecture decisions
- ✅ Fewer rejected PRs, less back-and-forth

## 🐉 Want More?

This is a free sample from [**Dohko's AI Dev Toolkit**](https://ai-dev-toolkit-five.vercel.app) — 100+ battle-tested prompts for developers. The full toolkit includes advanced AGENTS.md templates for monorepos, microservices, and multi-language projects.

[**Get the Full Toolkit → $9**](https://ai-dev-toolkit-five.vercel.app)
