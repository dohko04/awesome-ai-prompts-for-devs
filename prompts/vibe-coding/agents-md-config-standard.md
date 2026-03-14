# AGENTS.md Config Standard — Cross-Tool AI Coding Setup

> Set up the universal AGENTS.md config file to control AI coding agents across Claude Code, Amp, Devin, Zed, Cursor, and more — one file, every tool.

## The Prompt

```
You are an expert in AI coding agent configuration. Help me create an AGENTS.md 
file for my project that works across all major AI coding tools.

## My Project Context
- Language/framework: [YOUR_STACK]
- Repo structure: [MONO/MULTI/STANDARD]
- Team size: [SOLO/SMALL/LARGE]
- Primary AI tools: [CLAUDE_CODE/CURSOR/AMP/DEVIN/ZED]

## What I Need
Generate a production-ready AGENTS.md that includes:

1. **Project context** — What the project does, key architectural decisions
2. **Code style rules** — Formatting, naming conventions, patterns to follow
3. **File structure guidance** — Where things go, what not to touch
4. **Testing requirements** — What must be tested, how to run tests
5. **Forbidden patterns** — Anti-patterns, deprecated APIs, security no-gos
6. **Tool-specific sections** — Sections that specific tools will parse

## Output Format
Return a complete AGENTS.md file with clear sections and comments explaining 
which tools parse which sections. Include examples for at least 3 real rules.

## Compatibility Notes
Include comments for:
- Claude Code (reads AGENTS.md natively, nearest-file precedence)
- Amp/Sourcegraph (reads AGENTS.md, falls back to CLAUDE.md)  
- Devin (reads before every task)
- Cursor (.cursorrules compatibility bridge)
- Zed (agent system integration)
```

## Example Output (Partial)

```markdown
# AGENTS.md

## Project Overview
This is a Next.js 15 SaaS app with Supabase backend...

## Code Style
- Use TypeScript strict mode everywhere
- Prefer server components; mark 'use client' only when needed
- Never use `any` type — use `unknown` + type guards

## Testing
- Every new function needs a unit test in __tests__/
- Run: `npm test` before suggesting changes are complete
- Integration tests required for API routes
```

## Tools That Support AGENTS.md (March 2026)
| Tool | Support | Notes |
|------|---------|-------|
| Claude Code | ✅ Native | Nearest-file-in-directory precedence |
| Amp (Sourcegraph) | ✅ Native | Falls back to CLAUDE.md |
| Devin | ✅ Native | Reads before every task |
| Cursor | ⚡ Bridge | Via .cursorrules compatibility |
| Zed | ✅ Native | Agent system integration |
| Roo Code | ✅ Native | Confirmed adopter |
| Jules (Google) | ✅ Native | Confirmed adopter |
| Aider | ✅ Native | Confirmed adopter |

## Limitations of This Free Version

This starter gives you a basic AGENTS.md template. The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:

- 🔧 **Multi-tool AGENTS.md generator** — Generates optimized configs for your specific stack with per-tool tuning
- 📁 **Directory-level overrides** — Nested AGENTS.md strategy for monorepos (backend/, frontend/, infra/)
- 🔄 **Migration scripts** — Convert .cursorrules, .clinerules, CLAUDE.md to unified AGENTS.md
- 🧪 **Validation pipeline** — CI check that your AGENTS.md stays in sync with actual codebase
- 📊 **Agent behavior audit** — Track which rules agents follow vs ignore across tools

---

*Part of the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 130+ production-ready AI dev resources for $9*
