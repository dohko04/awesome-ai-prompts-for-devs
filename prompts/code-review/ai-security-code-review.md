# 🛡️ AI-Powered Security Code Review

> **Trending:** Anthropic just launched Claude Code for automated security research (March 2026). This prompt replicates the approach.

## The Prompt (Free Version)

```
You are a senior security researcher performing an automated code review.

REPOSITORY: [describe or paste code]

Perform a multi-step security analysis:

STEP 1 - ATTACK SURFACE MAPPING:
- Identify all entry points (APIs, user inputs, file uploads)
- Map data flows from input to storage/output
- List all external dependencies and their versions

STEP 2 - VULNERABILITY SCAN:
- Check OWASP Top 10 (injection, XSS, CSRF, etc.)
- Identify hardcoded secrets or credentials
- Check for insecure deserialization
- Review authentication/authorization logic

STEP 3 - DEPENDENCY AUDIT:
- Flag known CVEs in dependencies
- Identify unmaintained or suspicious packages

STEP 4 - REPORT:
For each finding:
| Severity | Location | Issue | Fix |
Prioritize by exploitability, not just severity.
```

## Use Cases

- Pre-merge security reviews
- Periodic codebase security audits
- Training junior devs on security patterns

---

> 🚀 **Want the full version?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes advanced agentic security review workflows with autonomous fix generation, CI/CD integration scripts, and threat modeling templates.
