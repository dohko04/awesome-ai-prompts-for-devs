# Copilot Autopilot Safety Guide ✈️

> VS Code 1.111 introduced **Autopilot mode** for Copilot Chat — the AI executes multi-step tasks autonomously, auto-approves tool calls, and auto-retries errors. This prompt helps you adopt it safely.

## The Prompt

```
You are a senior dev reviewing my Copilot Autopilot session configuration.

Context:
- VS Code 1.111+ with Copilot Chat Autopilot mode enabled
- Project type: [e.g., Node.js API, React app, Python ML pipeline]
- Team size: [solo / small team / enterprise]
- Sensitive files: [list paths that should NEVER be auto-modified]

Tasks:
1. Generate a `.vscode/settings.json` snippet that:
   - Enables Autopilot for safe operations (tests, linting, docs)
   - Keeps manual approval for: file deletion, dependency changes, config modifications
   - Sets appropriate retry limits (max 2 retries before stopping)

2. Create a pre-Autopilot checklist:
   - Git status clean? (uncommitted changes = risk)
   - Branch isolated? (never Autopilot on main)
   - Scope defined? (vague prompts + Autopilot = chaos)

3. Write 3 example Autopilot prompts that are SAFE:
   - Specific scope, clear success criteria, bounded changes

4. Write 3 example prompts that are DANGEROUS in Autopilot:
   - Explain why each could cause harm with auto-approval

Output format: Markdown with code blocks. Be specific, not generic.
```

## Example Output (abbreviated)

```json
// .vscode/settings.json
{
  "github.copilot.chat.agentPermissions": {
    "default": "autopilot",
    "file.delete": "manual",
    "terminal.execute": "manual",
    "package.install": "manual"
  },
  "github.copilot.chat.autopilot.maxRetries": 2
}
```

**Safe prompt:** "Add unit tests for all exported functions in `src/utils/` using vitest. Don't modify source files."

**Dangerous prompt:** "Refactor the entire auth system to use JWT instead of sessions." ← Autopilot will auto-approve every change across dozens of files.

## When to Use

- Setting up Autopilot for the first time
- Onboarding team members to autonomous AI coding
- Creating guardrails before enabling auto-approval

## Limitations of This Free Version

This gives you the safety foundation. The **PRO version** includes:
- Complete permission matrix for 15+ tool types
- Team-wide Autopilot policy templates (RBAC)
- Cost monitoring configs (token budget caps)
- Incident recovery playbook (when Autopilot goes wrong)
- CI/CD integration to validate Autopilot changes before merge

---

> 🔥 **Want the full Copilot Autopilot Production Pipeline?**  
> Get 107+ production-ready AI dev frameworks for just **$9** →  
> [**ai-dev-toolkit-five.vercel.app**](https://ai-dev-toolkit-five.vercel.app)
