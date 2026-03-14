# 🔍 Copilot CLI Code Review Workflow

> Get AI-powered code reviews directly in your terminal — never leave the command line to review PRs.

Based on GitHub Copilot's new CLI CodeReview agent (March 2026) — run `gh copilot review` to get instant code analysis in your terminal.

## The Prompt

```
You are a Terminal Code Review Workflow Architect. Help me set up an efficient CLI-based code review pipeline using GitHub Copilot's CLI review capabilities.

Given my setup:
- **Project type:** [e.g., monorepo, microservices, single app]
- **Languages:** [e.g., TypeScript, Python, Go]
- **Team size:** [e.g., solo, 3-5, 10+]
- **CI/CD:** [e.g., GitHub Actions, GitLab CI, none]
- **Review bottlenecks:** [e.g., slow reviews, missed bugs, inconsistent standards]

Design a CLI code review workflow that:

1. **Pre-Push Review**
   - Command to review staged changes before committing
   - Focus areas: security, performance, style consistency
   - Auto-generate commit message from review summary

2. **PR Review Pipeline**
   - Single command to review entire PR diff
   - Severity classification (critical/warning/info)
   - Output format: terminal table + optional markdown for PR comments

3. **Review Checklist Automation**
   - Map team coding standards to review rules
   - Auto-check: error handling, test coverage gaps, API contract changes
   - Flag files that need human review (complex logic, security-sensitive)

4. **Shell Integration**
   - Git aliases for one-command reviews
   - Pre-commit hook integration
   - Output piping to clipboard/file for async review

Provide ready-to-use shell commands and git config snippets.
```

## Quick Setup

```bash
# Install/update GitHub CLI with Copilot extension
gh extension install github/gh-copilot

# Review current changes
gh copilot review

# Review specific PR
gh copilot review --pr 42

# Git alias for pre-commit review
git config --global alias.ai-review '!gh copilot review --diff HEAD'

# Pre-commit hook
echo '#!/bin/sh
echo "🔍 Running Copilot review..."
gh copilot review --diff HEAD --severity critical
if [ $? -ne 0 ]; then
  echo "❌ Critical issues found. Fix before committing."
  exit 1
fi' > .git/hooks/pre-commit && chmod +x .git/hooks/pre-commit
```

## Review Output Example

```
┌─────────────┬──────────┬────────────────────────────────────┐
│ File        │ Severity │ Finding                            │
├─────────────┼──────────┼────────────────────────────────────┤
│ auth.ts:42  │ 🔴 CRIT  │ SQL injection via string concat    │
│ api.ts:18   │ 🟡 WARN  │ Missing error handler on async     │
│ utils.ts:7  │ 🔵 INFO  │ Consider using optional chaining   │
└─────────────┴──────────┴────────────────────────────────────┘
```

## When to Use This

- **Solo devs** — get a "second pair of eyes" without waiting
- **Fast PRs** — triage before requesting human review
- **Pre-commit** — catch issues before they hit CI
- **Learning** — understand why code patterns are flagged

## Limitations of This Free Version

- Basic single-command workflows only
- No multi-model comparison (Copilot vs Claude vs GPT)
- No team-wide standards enforcement pipeline
- No cost optimization or token tracking

---

> 🔥 **Want the full production pipeline?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes multi-model review orchestration, team standards YAML configs, CI/CD integration templates, cost optimization, and 149+ more production-ready resources.
