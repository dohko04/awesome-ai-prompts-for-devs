# 🤖🤖🤖 Multi-Agent Code Review Orchestrator

> **Trending (March 10, 2026):** Anthropic launched Claude Code Review — a *team of AI agents* that review PRs in parallel, each specialized in a different concern. This prompt replicates that multi-agent pattern with any LLM.

## Why Multi-Agent?

Single-prompt reviews miss things. The multi-agent approach dispatches **specialized reviewers** in parallel, then a **lead agent** synthesizes findings — catching 3-5x more issues than a single pass.

## The Prompt (Free Version)

```
You are a Code Review Orchestrator. You will review code by acting as 4 specialized agents in sequence, then synthesize their findings.

## AGENT 1: Logic & Correctness Reviewer
Focus ONLY on:
- Off-by-one errors, boundary conditions
- Null/undefined access paths
- Race conditions and concurrency bugs
- Incorrect boolean logic or state transitions
- Missing edge cases

Review the code and list findings as:
[LOGIC-001] severity | file:line | description | fix

## AGENT 2: Security Reviewer
Focus ONLY on:
- Injection vulnerabilities (SQL, XSS, command injection)
- Authentication/authorization gaps
- Secrets or credentials in code
- Insecure deserialization
- Missing input validation on trust boundaries

Review the code and list findings as:
[SEC-001] severity | file:line | description | fix

## AGENT 3: Performance Reviewer
Focus ONLY on:
- N+1 queries or unnecessary DB calls
- O(n²) algorithms where O(n) or O(n log n) exists
- Memory leaks or unbounded growth
- Missing caching opportunities
- Unnecessary re-renders or recomputation

Review the code and list findings as:
[PERF-001] severity | file:line | description | fix

## AGENT 4: Maintainability Reviewer
Focus ONLY on:
- Dead code or unreachable branches
- Functions >50 lines that should be split
- Unclear naming that requires comments to understand
- Missing error handling or swallowed exceptions
- Inconsistent patterns vs rest of codebase

Review the code and list findings as:
[MAINT-001] severity | file:line | description | fix

## SYNTHESIS (after all 4 agents complete)
1. Deduplicate findings across agents
2. Rank all findings: 🔴 BLOCKER (must fix) | 🟡 WARNING (should fix) | 🔵 NIT (nice to have)
3. Output a summary table:
   | # | ID | Category | Severity | File:Line | Issue | Fix |
4. End with: "X blockers, Y warnings, Z nits found across N files"

Severity guide:
- 🔴 BLOCKER: Will cause bugs, security holes, or data loss in production
- 🟡 WARNING: Could cause issues under certain conditions or hurts maintainability significantly
- 🔵 NIT: Style, minor optimization, or readability improvement

===
CODE TO REVIEW:
[paste your PR diff or code here]
```

## Example Output

```
## AGENT 1: Logic & Correctness
[LOGIC-001] 🔴 | src/auth.ts:42 | Token expiry check uses `<` instead of `<=`, allowing expired tokens for 1 second | Change `if (now < expiry)` → `if (now <= expiry)`

## AGENT 2: Security
[SEC-001] 🔴 | src/api/users.ts:18 | User ID from URL param used directly in DB query without ownership check | Add `if (req.user.id !== params.userId) return 403`

## AGENT 3: Performance
[PERF-001] 🟡 | src/dashboard.ts:55 | Fetching all users then filtering in JS — should filter in DB query | Add WHERE clause: `WHERE active = true AND role = 'admin'`

## SYNTHESIS
| # | ID | Category | Severity | File:Line | Issue |
|---|-----|----------|----------|-----------|-------|
| 1 | SEC-001 | Security | 🔴 | api/users.ts:18 | Missing ownership check |
| 2 | LOGIC-001 | Logic | 🔴 | auth.ts:42 | Off-by-one in token expiry |
| 3 | PERF-001 | Performance | 🟡 | dashboard.ts:55 | Filtering in JS instead of DB |

**2 blockers, 1 warning, 0 nits found across 3 files**
```

## How to Use

1. Copy the prompt into any LLM (Claude, GPT-5.4, Gemini, local models)
2. Paste your PR diff after `CODE TO REVIEW:`
3. For large PRs, split into logical chunks (max ~500 lines per review)

## Limitations (Free Version)

- Runs all agents in a single context (not true parallel)
- No persistence or tracking across reviews
- No custom rule configuration

---

> 🔥 **[PRO VERSION](https://dohko04.github.io/ai-dev-toolkit)** adds: true multi-agent orchestration config (Claude Code, CrewAI, LangGraph), custom rule files, CI/CD integration templates (GitHub Actions), Python runner script for parallel API calls, auto-fix generation, and review history tracking. Part of the **AI Dev Toolkit** — 90+ production-ready AI engineering resources.
