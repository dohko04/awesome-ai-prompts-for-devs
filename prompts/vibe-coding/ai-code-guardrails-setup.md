# 🛡️ AI Code Generation Guardrails Setup

> Set up automated guardrails so AI-generated code doesn't break your codebase. Essential for teams using Cursor, Claude Code, Copilot, or Codex in 2026.

## The Prompt

```
You are an AI code quality guardian. I need you to create a complete guardrails setup for AI-generated code in my project.

**My stack:** [YOUR STACK - e.g., TypeScript/Next.js/PostgreSQL]
**AI tools I use:** [e.g., Claude Code, Cursor, Copilot]
**Team size:** [e.g., 5 engineers]

Generate the following:

1. **Pre-commit hooks** (using lint-staged + husky) that catch common AI code smells:
   - Unused imports and dead code AI tends to leave behind
   - Console.log statements meant for debugging
   - Hardcoded secrets or API keys
   - TODO comments from AI that were never resolved
   - Overly complex functions (cyclomatic complexity > 10)

2. **AI-specific ESLint rules** (or equivalent for my language):
   - Ban patterns AI frequently generates wrong (e.g., `any` types in TS)
   - Enforce naming conventions AI often ignores
   - Flag suspiciously large generated files (>300 lines)

3. **CI check script** that:
   - Detects if >60% of a PR was AI-generated (via git-diff heuristics)
   - Requires extra review for AI-heavy PRs
   - Runs property-based tests on AI-generated functions
   - Checks for AI hallucinated imports (packages that don't exist)

4. **PR template** with AI disclosure section:
   - Which parts were AI-generated?
   - Which AI tool was used?
   - Were outputs manually verified?

Output everything as ready-to-copy config files with install commands.
```

## Example Output

The AI will generate:
- `.husky/pre-commit` hook
- `.lintstagedrc.js` config
- `eslint-ai-guardrails.js` custom rules
- `scripts/ai-pr-check.sh` CI script
- `.github/PULL_REQUEST_TEMPLATE.md`

## Why This Matters (March 2026)

GitHub's Octoverse data shows AI-generated code now accounts for **40%+ of new code** in many repos. Without guardrails, teams ship hallucinated imports, dead code, and security issues. This prompt gives you a production-ready safety net in minutes.

## Pro Tips

- Run the CI check in **warning mode** first — don't block PRs until your team adjusts
- Add your project's specific anti-patterns to the ESLint rules
- The hallucinated import check alone saves hours of debugging

---

> 💡 **Want the complete version?** The [Full AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes guardrail configs for 8 languages, team dashboard templates, and a Slack bot that alerts on AI code quality drops.
