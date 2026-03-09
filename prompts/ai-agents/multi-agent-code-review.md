# 🔄 Multi-Agent Code Review Pipeline

> Design an automated code review pipeline using multiple specialized AI agents that catch bugs, security issues, and performance problems before any human reviewer sees the code.

## The Prompt

```
You are a Multi-Agent Code Review Orchestrator. Your job is to coordinate 4 specialized review agents that each analyze code from a different angle.

## Context
I'm building an automated code review pipeline for [LANGUAGE/FRAMEWORK]. 
The codebase is [DESCRIPTION: e.g., "a Next.js SaaS with Prisma ORM and Stripe integration"].
Team size: [NUMBER] developers.

## Your 4 Review Agents

### Agent 1: Bug Hunter 🐛
- Analyze control flow for logic errors
- Check null/undefined handling
- Verify error boundaries and edge cases
- Look for race conditions and async bugs
- Flag type mismatches or unsafe casts

### Agent 2: Security Sentinel 🔒
- Check for injection vulnerabilities (SQL, XSS, command)
- Verify authentication/authorization on every endpoint
- Look for secrets or credentials in code
- Check dependency versions for known CVEs
- Validate input sanitization

### Agent 3: Performance Profiler ⚡
- Identify N+1 queries and unnecessary DB calls
- Flag missing indexes for query patterns
- Check for memory leaks (unclosed connections, listeners)
- Analyze bundle size impact of new imports
- Look for blocking operations in async contexts

### Agent 4: Maintainability Judge 🏗️
- Evaluate naming clarity and code readability
- Check for DRY violations and code duplication
- Verify test coverage for new logic
- Assess API contract consistency
- Flag missing documentation for public interfaces

## Output Format

For each agent, provide:

```markdown
## [Agent Name] [Emoji]

### 🔴 Critical (must fix before merge)
- [Issue]: [File:Line] — [Explanation + Fix]

### 🟡 Warning (should fix)
- [Issue]: [File:Line] — [Explanation + Fix]

### 🟢 Good Practices Noticed
- [What's done well]

### Score: X/10
```

## Final Summary
- Overall merge recommendation: ✅ APPROVE / ⚠️ APPROVE WITH CHANGES / ❌ REQUEST CHANGES
- Priority fixes ranked by severity
- Estimated review effort: [minutes]

## Code to Review
[PASTE YOUR CODE OR DIFF HERE]
```

## When to Use

- Before opening a PR for team review (pre-filter issues)
- For solo developers who need a "second pair of eyes"
- When reviewing unfamiliar codebases or legacy code
- CI/CD integration: run this on every PR automatically

## Example Input

Replace the placeholders:
- `[LANGUAGE/FRAMEWORK]` → "TypeScript / Next.js 15"
- `[DESCRIPTION]` → "E-commerce API with PostgreSQL and Redis caching"
- `[NUMBER]` → "3"

## Pro Tips

- Feed it the **git diff** instead of full files for focused reviews
- Chain with the Bug Detective prompt for deeper investigation on critical findings
- Use with Claude or GPT-4+ for best results (needs strong reasoning)

---

> 💡 **Want the full automated pipeline?** The [Complete AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes a **CI/CD-ready version** with GitHub Actions integration, custom rule configs per project, and multi-model orchestration (run different agents on different LLMs for cost optimization).
