# ⚡ Cursor + Claude Code Dual Workflow

> The 2026 power setup: Use Cursor for speed, Claude Code for depth. This prompt configures both tools to work on the same project without conflicts.

## The Prompt (for Claude Code)

```
I use Cursor IDE + Claude Code on this project simultaneously. Help me set up
a conflict-free dual workflow.

My project: <brief description>
My stack: <stack>

Generate:

1. **`.cursorrules` file** — Rules for Cursor's AI to follow in this project.
   Include: coding style, file conventions, what Cursor should/shouldn't touch,
   preferred patterns, import conventions.

2. **`AGENTS.md` section** — A "Tool Boundaries" section defining:
   - What Claude Code handles (refactoring, architecture, tests, complex multi-file changes)
   - What Cursor handles (inline completions, single-file edits, quick fixes)
   - Shared conventions both must follow

3. **`.claude/settings.json`** — Claude Code project settings with:
   - Allowed tools/commands
   - File patterns to watch
   - Auto-approve patterns for safe operations

4. **Git workflow** — Branch naming and commit conventions so I can tell
   which tool made which changes:
   - Cursor changes: conventional commits, small atomic commits
   - Claude Code changes: prefixed with [claude] in commit message

Be specific to my project. Every config should be copy-paste ready.
```

## When to Use Which Tool

| Task | Best Tool | Why |
|------|-----------|-----|
| Autocomplete while typing | Cursor | Real-time, low latency |
| Generate a function from comment | Cursor Composer | Inline, stays in flow |
| Refactor 10+ files | Claude Code | Multi-file reasoning |
| Write comprehensive tests | Claude Code | Understands full context |
| Quick bug fix | Cursor | Tab-complete the fix |
| Architecture changes | Claude Code | Plans before executing |
| Explore unfamiliar code | Cursor Chat | Quick Q&A in sidebar |
| CI/CD pipeline setup | Claude Code | Needs system context |

## Pro Tips

1. **Never run both simultaneously on the same files** — Git conflicts guaranteed
2. **Claude Code for planning, Cursor for executing** — Best of both worlds
3. **Share context via files, not memory** — Both tools read AGENTS.md and .cursorrules
4. **Use git stash** before switching tools on uncommitted changes

## 🐉 Want More?

This is a free sample from [**Dohko's AI Dev Toolkit**](https://ai-dev-toolkit-five.vercel.app). The full toolkit includes complete `.cursorrules` templates for React, Next.js, Python, Go, and Rust projects, plus advanced Claude Code workflows.

[**Get the Full Toolkit → $9**](https://ai-dev-toolkit-five.vercel.app)
