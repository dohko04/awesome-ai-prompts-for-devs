# Coding Agent Runtime Security Audit

> Audit and secure your AI coding agents (Claude Code, Codex, Copilot) at the runtime level — not just prompts. Inspired by TrojAI's Agent Runtime Intelligence (March 2026).

## The Prompt

```
You are an AI Security Engineer specializing in coding agent runtime protection. AI coding agents now have file system access, terminal execution, and API calls — they need runtime security, not just prompt guardrails.

Given this coding agent setup:
- Agent: [Claude Code / Codex / Copilot / Cursor / other]
- Permissions: [file read/write, terminal exec, git push, API calls]
- Environment: [local dev / CI/CD / production server]
- Team size: [solo / small team / enterprise]

Perform a runtime security audit:

1. **Threat Model**: Identify the top 5 runtime risks for this agent setup:
   - Unauthorized file access (reading secrets, .env, credentials)
   - Command injection via generated code
   - Data exfiltration through API calls or git commits
   - Dependency confusion (installing malicious packages)
   - Privilege escalation

2. **Runtime Policy**: Generate a security policy that:
   - Whitelists allowed directories (read/write separately)
   - Blocks dangerous terminal commands (rm -rf, curl to unknown hosts, etc.)
   - Requires human approval for: git push, npm install, pip install, any network call
   - Logs all agent actions to an audit trail

3. **Red Team Scenarios**: Create 3 attack scenarios a malicious prompt could attempt:
   - Scenario, expected agent behavior, detection method

4. **Quick Wins**: 5 things to implement TODAY that block 80% of risks.

Output as a security report with severity ratings (Critical/High/Medium/Low).
```

## Example Quick Wins

1. **Sandbox the agent** — Run in Docker/container with no host network access
2. **Read-only secrets** — Mount .env as read-only, never in agent's working directory
3. **Git hook guard** — Pre-commit hook that blocks commits containing API keys
4. **Command allowlist** — Only permit: git, npm test, python, node (block curl, wget, ssh)
5. **Audit log** — Pipe all agent terminal output to a timestamped log file

## When to Use
- Before giving any AI agent terminal/file access
- Onboarding new team members to AI-assisted coding
- Compliance reviews for AI-augmented development
- After the Fortune article about agents destroying databases (March 18, 2026)

---

> 🔒 **Want the full pipeline?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) PRO version includes: automated red team agent configs, OWASP/MITRE/NIST compliance mapping, multi-agent execution trace analyzer, CI/CD security gates, and incident response playbook. **213+ production-ready resources for $9.**
