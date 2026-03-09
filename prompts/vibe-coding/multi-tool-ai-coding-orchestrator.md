# 🎛️ Multi-Tool AI Coding Orchestrator

Most devs in 2026 juggle 2-4 AI coding tools (Cursor, Claude Code, Copilot, Windsurf). This prompt helps you design an optimal workflow that uses each tool for what it's best at — instead of fighting them.

## The Prompt

```
You are an expert developer who has mastered every major AI coding tool in 2026. I want to set up an optimized multi-tool workflow for my project.

My current setup:
- **Tools I have:** {TOOLS: e.g., Cursor Pro, Claude Code, GitHub Copilot, Windsurf}
- **Project type:** {PROJECT_TYPE: e.g., full-stack web app, CLI tool, API service}
- **Tech stack:** {STACK: e.g., TypeScript, Next.js, PostgreSQL}
- **Team size:** {TEAM_SIZE: solo | 2-5 | 5+}

Design my optimal AI coding workflow:

### 1. Tool Assignment Matrix
For each development task, tell me which tool to use and WHY:
| Task | Best Tool | Why | Fallback |
|------|-----------|-----|----------|
| Greenfield feature coding | ? | ? | ? |
| Bug investigation & fixes | ? | ? | ? |
| Refactoring large files | ? | ? | ? |
| Writing tests | ? | ? | ? |
| Code review | ? | ? | ? |
| Terminal/DevOps tasks | ? | ? | ? |
| Multi-file architecture changes | ? | ? | ? |
| Quick inline completions | ? | ? | ? |
| Documentation | ? | ? | ? |

### 2. Context Sharing Strategy
- How do I keep context consistent across tools?
- What files should EVERY tool have access to? (AGENTS.md, .cursorrules, etc.)
- Show me a universal project context file that works across all tools.

### 3. Workflow Patterns
Design 3 concrete workflows:
a) **Feature Development Flow**: tool A for scaffold → tool B for implementation → tool C for review
b) **Bug Fix Flow**: fastest path from error to fix using my tools
c) **Refactor Flow**: safe large-scale changes with AI assistance

### 4. Config Files
Generate the config/rules files I need:
- `.cursorrules` or `.cursor/rules/` (if using Cursor)
- `AGENTS.md` or `CLAUDE.md` (if using Claude Code)
- `.github/copilot-instructions.md` (if using Copilot)
- Any other tool-specific configs

Make them consistent — same coding standards, same patterns, same voice.

### 5. Anti-Patterns to Avoid
- When does using multiple tools HURT productivity?
- Context switching costs and how to minimize them.
- When to stick with one tool for an entire session.

Output everything as actionable configs and workflows I can implement TODAY.
```

## Example Usage

```
Tools: Cursor Pro, Claude Code (terminal), GitHub Copilot
Project: SaaS app with Next.js 15, tRPC, Drizzle ORM, PostgreSQL
Stack: TypeScript, React, Node.js
Team: solo developer
```

## Tips

- Don't use all tools for everything — specialize each one.
- Keep a single source of truth for coding rules, then adapt per tool.
- Terminal-based tools (Claude Code) excel at multi-file changes and git operations.
- IDE tools (Cursor, Copilot) are better for in-flow completions and single-file edits.

---

> 🚀 **Get pre-built config files for every AI coding tool.** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes optimized .cursorrules, AGENTS.md templates, Copilot configs, and multi-tool workflow guides — tested across real projects.
