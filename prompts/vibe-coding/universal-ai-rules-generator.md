# 🎯 Universal AI Coding Rules Generator

> Generate optimized rules/instructions files for ANY AI coding tool — Cursor (.cursor/rules), Claude Code (CLAUDE.md), Windsurf, Copilot, Cline, Aider — from a single project description. Stop writing rules from scratch for every tool.

## The Prompt

```
You are an AI Coding Rules Expert. Generate tool-specific configuration files that make AI coding assistants work 10x better with my project.

## My Project
- Name: [PROJECT NAME]
- Stack: [e.g., "Next.js 15, TypeScript, Tailwind, Prisma, PostgreSQL"]
- Package manager: [npm/pnpm/yarn/bun]
- Monorepo: [yes/no, tool if yes: turborepo/nx/etc]
- Testing: [framework: vitest/jest/playwright/etc]
- Deployment: [Vercel/AWS/Docker/etc]
- Key patterns: [e.g., "Server Components by default, tRPC for API, Zustand for state"]
- Conventions: [e.g., "kebab-case files, barrel exports, co-located tests"]

## Generate For: [TOOL — pick one or "all"]

### Option A: Cursor Rules (.cursor/rules/*.mdc)
Generate glob-targeted rule files:
- `general.mdc` — Project-wide conventions, tech stack, file structure
- `frontend.mdc` — Component patterns, styling, state management
- `backend.mdc` — API patterns, DB access, error handling
- `testing.mdc` — Test patterns, mocking, coverage expectations

Each file must use the frontmatter format:
```
---
description: [when this rule applies]
globs: [file patterns]
alwaysApply: [true/false]
---
[rules content]
```

### Option B: Claude Code (CLAUDE.md)
Generate a single CLAUDE.md with:
- Project overview & architecture
- Key commands (build, test, lint, deploy)
- Code style & conventions
- Common patterns with examples
- What to avoid (anti-patterns)
- File structure reference

### Option C: AGENTS.md (Multi-agent / Claude Code)
Generate AGENTS.md for autonomous coding:
- Task decomposition rules
- File ownership boundaries
- Git workflow (branch naming, commit format)
- Testing requirements before marking done
- Review checklist

### Option D: Windsurf / Copilot Instructions
Generate `.windsurfrules` or `.github/copilot-instructions.md`:
- Adapted format for each tool's conventions
- Same content, different structure

## Quality Requirements
- Rules must be SPECIFIC to my stack (no generic "write clean code")
- Include concrete examples of DO and DON'T
- Reference actual file paths and patterns from my project structure
- Keep each rule file under 500 lines (tools have context limits)
- Prioritize: most impactful rules first

## Output
For each file, provide:
1. File path (where to save it)
2. Complete file content
3. One-line explanation of what it does
```

## When to Use

- Starting a new project with AI coding tools
- Migrating between AI tools (Cursor → Claude Code, etc.)
- Onboarding new team members (rules = documentation)
- After major refactors that change project conventions

## Example Input

```
- Name: ShipFast
- Stack: Next.js 15, TypeScript 5.4, Tailwind v4, Drizzle ORM, Turso DB
- Package manager: pnpm
- Monorepo: no
- Testing: Vitest + Playwright
- Deployment: Vercel
- Key patterns: App Router, Server Actions, Drizzle for DB, Lucia for auth
- Conventions: kebab-case files, src/ directory, co-located tests as *.test.ts
- Generate for: all
```

## Pro Tips

- Regenerate rules when you upgrade major dependencies
- Keep rules in version control — they're documentation
- Different team members can use different tools with equivalent rules
- Test rules by asking the AI to scaffold a new feature and checking if it follows conventions

---

> 💡 **Want pre-built rule sets for popular stacks?** The [Complete AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes **15+ ready-made rule configurations** for Next.js, Django, Rails, FastAPI, Go, Rust, and more — plus a rule testing framework that validates your AI assistant actually follows them.
