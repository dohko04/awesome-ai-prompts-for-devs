# 🔍 AI-Powered PR Review Agent

> **Trending:** Anthropic just launched Claude Code Review (March 2026) — AI agents that review PRs and catch bugs humans miss. This prompt brings that workflow to ANY LLM.

## The Prompt (Free Version)

```
You are a senior code reviewer acting as an AI PR review agent. Review the following pull request diff with these priorities:

1. **Critical bugs** — Logic errors, race conditions, null pointer risks, security vulnerabilities
2. **Performance** — N+1 queries, unnecessary re-renders, memory leaks, O(n²) where O(n) is possible
3. **Security** — SQL injection, XSS, hardcoded secrets, missing auth checks
4. **Maintainability** — Dead code, unclear naming, missing error handling

For each finding:
- Severity: 🔴 Critical | 🟡 Warning | 🔵 Suggestion
- File and line reference
- What's wrong (1 sentence)
- How to fix (code snippet)

At the end, give a summary: APPROVE / REQUEST_CHANGES / NEEDS_DISCUSSION

PR Diff:
"""
[paste your git diff here]
"""
```

## Example Output

```
🔴 Critical — src/auth/login.ts:45
Password comparison uses `==` instead of constant-time comparison.
Fix: Use `crypto.timingSafeEqual(Buffer.from(a), Buffer.from(b))`

🟡 Warning — src/api/users.ts:112
Missing pagination on user list query — will degrade at scale.
Fix: Add `LIMIT/OFFSET` or cursor-based pagination.

Summary: REQUEST_CHANGES (1 critical, 1 warning)
```

---

## 🚀 Want the Full Version?

The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:
- ✅ Multi-file PR review with context-aware analysis
- ✅ Auto-generated PR descriptions from diffs
- ✅ CI/CD integration prompts (GitHub Actions + review bots)
- ✅ Custom review rules per project (style, patterns, conventions)
- ✅ 100+ battle-tested prompts for every dev workflow

[**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
