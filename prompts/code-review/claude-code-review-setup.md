# 🤖 Claude Code Review — REVIEW.md Starter Template

> Configure Anthropic's new multi-agent PR review system (launched March 9, 2026) to catch logic bugs, not just style issues.

## What This Is

Claude Code Review dispatches parallel AI agents to review your PRs from different angles — logic, security, performance, and more. Teams customize it via a `REVIEW.md` file in their repo root.

This is a production-ready starter template.

## REVIEW.md Template

Create this file at your repo root:

```markdown
# Code Review Policy

## Review Focus (Priority Order)
1. **Logic errors** — wrong comparisons, off-by-one, race conditions
2. **Security** — injection, auth bypass, secrets in code, XSS
3. **Data integrity** — missing transactions, cascade deletes, unvalidated writes
4. **Breaking changes** — public API changes without versioning
5. **Performance** — N+1 queries, unbounded loops, memory leaks

## Skip These (Don't Comment On)
- Formatting and style (handled by linters)
- Import ordering
- Variable naming preferences (unless genuinely confusing)
- Comments suggesting "add more comments"

## Severity Levels
- 🔴 **Blocker**: Must fix before merge. Logic errors, security vulnerabilities, data loss risks.
- 🟡 **Warning**: Should fix. Performance issues, missing error handling, unclear edge cases.
- 💡 **Suggestion**: Nice to have. Better patterns, readability improvements.

## Context Rules
- Check adjacent files when reviewing a function change
- Flag if tests are missing for new logic paths
- Note if error messages are user-facing and unclear
```

## Quick Setup

1. Add `REVIEW.md` to your repo root
2. Add `CLAUDE.md` with project context (tech stack, conventions, architecture)
3. Enable Claude Code Review in your Team/Enterprise settings
4. Install the GitHub App
5. Reviews run automatically on every new PR

## Tips

- **Be specific in REVIEW.md** — vague rules produce vague reviews
- **Use CLAUDE.md for context** — tell it your tech stack, DB schema patterns, auth flow
- **Cost: ~$15-25/review** — focus on repos where bugs are expensive

---

## Want the Full Version?

The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:
- 🔧 Complete REVIEW.md framework with per-language policies
- 📋 CLAUDE.md architecture template for maximum review context
- 💰 Cost optimization guide (reduce reviews from $25 to $8)
- 🏗️ Team rollout playbook (phased adoption, metrics tracking)
- 🔀 GitHub Actions fallback for non-Team/Enterprise plans

[← Back to Code Review](README.md) · [← All Prompts](../../README.md)
