# BloodHound Identity Attack Path Audit for AI Agent Infrastructure

> **FREE starter** — Audit identity attack paths across GitHub, Okta, and cloud environments where AI agents operate. Inspired by SpecterOps BloodHound OpenGraph (March 2026).

## The Prompt

```
You are an identity security architect specializing in AI agent infrastructure.

I need to audit identity attack paths in my environment where AI agents have credentials and permissions.

My setup:
- Identity provider: [Okta / Azure AD / Google Workspace]
- Code hosting: [GitHub / GitLab]
- AI agents running: [list agents — e.g., Codex, Claude Code, GitHub Actions bots]
- Cloud: [AWS / GCP / Azure]

Perform this audit:

1. **Agent Identity Inventory**
   - List all service accounts, API keys, and tokens used by AI agents
   - Map each agent to its permission scope (repos, cloud resources, secrets)
   - Flag over-privileged agents (admin when read-only suffices)

2. **Cross-Platform Attack Path Analysis**
   - Identify paths where compromising one agent credential leads to lateral movement
   - Example: GitHub bot token → repo access → secrets in CI → cloud admin
   - Map IdP → code platform → cloud privilege escalation chains

3. **Quick Remediation Checklist**
   - [ ] Rotate all agent tokens older than 90 days
   - [ ] Apply least-privilege to every agent service account
   - [ ] Enable MFA on all human accounts that manage agents
   - [ ] Separate agent credentials from developer credentials
   - [ ] Audit GitHub App permissions (remove unused scopes)

Output a risk-scored table:
| Agent | Identity Type | Permissions | Attack Path Risk | Fix |
```

## When to Use

- Before deploying new AI coding agents to your org
- After security incidents involving compromised tokens
- Quarterly identity hygiene reviews

## What You Get (Free vs Pro)

| Feature | Free (This) | Pro |
|---------|------------|-----|
| Basic audit prompt | ✅ | ✅ |
| Automated scanner script | ❌ | ✅ Python scanner |
| BloodHound/OpenGraph integration | ❌ | ✅ Custom queries |
| CI/CD security gates | ❌ | ✅ GitHub Actions |
| Compliance mapping (SOC2/ISO) | ❌ | ✅ Full mapping |
| Grafana attack path dashboard | ❌ | ✅ JSON dashboard |

---

**🔒 Want the full Identity Attack Path Security Pipeline?** Get the production version with automated scanning, BloodHound query templates, CI/CD gates, and compliance dashboards → [AI Dev Toolkit Pro](https://ai-dev-toolkit-five.vercel.app)
