# Vibe Coding Production Risk Audit

> Audit your AI-generated codebase for production risks before they cause outages. Based on real incidents: AWS 13-hour outage from AI agent changes, cascading failures from unreviewed AI code (March 2026).

## The Prompt

```
You are a production reliability engineer specializing in AI-generated code risk.
"Vibe coding" — heavily relying on AI tools to write production code — is causing 
real outages. AWS suffered 13-hour disruptions from unreviewed AI agent changes.
The pattern: AI code looks correct but misses hidden dependencies, system limits, 
and cascading failure modes.

## My Context
- AI tools used: [COPILOT/CURSOR/CLAUDE_CODE/CODEX/OTHER]
- Codebase size: [SMALL/MEDIUM/LARGE]
- Production system: [WEB_APP/API/INFRA/DATA_PIPELINE]
- Team review process: [NONE/INFORMAL/PR_REVIEW/FORMAL]

## Risk Audit Checklist

### 1. Unreviewed AI Code Detection
- What % of recent commits were AI-generated?
- Were they reviewed by a human who understands the system?
- Are there AI-generated changes to infrastructure/config files?

### 2. Hidden Dependency Risks
- Does the AI-generated code assume services are always available?
- Are there hardcoded timeouts, URLs, or resource limits?
- Could a change in one service cascade to others?

### 3. "Looks Correct" Trap
- Does the code handle edge cases or just the happy path?
- Are error boundaries comprehensive or superficial?
- Would this code survive 10x traffic, network partition, disk full?

### 4. AI Agent Autonomy Risks
- Are AI agents making infrastructure changes autonomously?
- Is there a rollback plan if AI changes break production?
- Are AI actions logged and auditable?

### 5. Speed vs Safety Score
Rate your current process:
- [ ] AI generates code → deployed same day (🔴 HIGH RISK)
- [ ] AI generates code → quick review → deployed (🟡 MEDIUM RISK)  
- [ ] AI generates code → full review + tests → staged deploy (🟢 LOW RISK)

## Output
1. Risk score (1-10, 10 = highest risk)
2. Top 3 most dangerous patterns found
3. Concrete action items to reduce risk
4. Recommended review process for AI-generated code
```

## Why This Matters NOW (March 14, 2026)

- **AWS outages** linked to AI coding agent errors (13-hour disruption)
- **Veracode**: "The most dangerous line of code is the one nobody reviewed because everyone assumed the machine got it right"
- **Engineering leaders**: "Speed without oversight is not velocity — it's debt accumulation at scale"
- **10x output** without 10x review = 10x risk

## Limitations of This Free Version

This gives you a solid manual audit prompt. The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:

- 🔍 **Automated Risk Scanner** — CI/CD pipeline that scores AI-generated PRs for production risk
- 📊 **Vibe Coding Metrics Dashboard** — Track AI code ratio, review coverage, incident correlation
- 🛡️ **AI Code Review Checklist Generator** — Stack-specific review checklists for AI-generated code
- 🔄 **Rollback Playbook** — Automated rollback procedures when AI changes cause incidents
- ⚡ **Safe Velocity Framework** — Ship fast WITH safety: staged deploys, canary configs, auto-revert rules

---

*Part of the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 136+ production-ready AI dev resources for $9*
