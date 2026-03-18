# 📋 AGENTS.md Universal Config Generator

> **Trending:** AGENTS.md adoption exploding (March 2026) — the universal config file now natively parsed by Cursor, Claude Code, Copilot, Windsurf, and more. One file to rule all your AI coding agents.

## The Prompt

```
You are an AGENTS.md Configuration Expert. Generate a production-ready AGENTS.md file for my project that works across ALL major AI coding agents.

## My Project
- Language: [TypeScript/Python/Go/Rust/etc.]
- Framework: [Next.js/FastAPI/etc.]
- Monorepo: [yes/no]
- AI tools I use: [Cursor, Claude Code, Copilot, Windsurf, etc.]
- Team size: [solo / 2-5 / 5-20 / 20+]
- Key conventions: [testing approach, naming, architecture patterns]

## Generate AGENTS.md With:

### 1. Project Context Section
- What this project does (1 paragraph)
- Architecture overview (key directories, patterns)
- Tech stack with versions

### 2. Coding Standards
- Naming conventions (variables, files, components)
- Error handling patterns
- Testing requirements (coverage, frameworks)
- Import ordering rules

### 3. AI Agent Rules
- Files/directories AI should NEVER modify
- Files AI should ALWAYS read before changes
- Required review patterns (security-sensitive areas)
- Max file size for AI-generated code

### 4. Tool-Specific Overrides
- Cursor: composer preferences, tab behavior
- Claude Code: auto-accept boundaries, memory hints
- Copilot: suggestion style, languages
- Windsurf: cascade preferences

### 5. Security Boundaries
- Secrets patterns to never generate/expose
- API endpoints that need human review
- Database migration rules

Output as a single, well-commented AGENTS.md file ready to commit.
```

## When to Use
- Starting a new project with AI coding tools
- Onboarding team members to your AI workflow
- Standardizing AI behavior across multiple tools
- Migrating from tool-specific configs (.cursorrules, CLAUDE.md) to universal

## Key Benefit
One AGENTS.md replaces: `.cursorrules` + `CLAUDE.md` + `copilot-instructions.md` + `.windsurfrules`

## Tags
`vibe-coding` `configuration` `agents-md` `multi-tool` `standards`

---

> 🔥 **Want the full AGENTS.md Production Pipeline?** 15 industry-specific templates, team governance framework, CI/CD validation, auto-sync across tools, and migration scripts → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
