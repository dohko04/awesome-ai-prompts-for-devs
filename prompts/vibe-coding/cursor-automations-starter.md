# Cursor Automations — Event-Driven AI Agent Starter

> **What:** Set up Cursor Automations to auto-trigger AI agents on GitHub PRs, Slack messages, Linear issues, cron schedules, and webhooks.
>
> **Why:** Code output from AI has exploded — but review, monitoring, and maintenance haven't kept up. Cursor Automations closes that gap with always-on agents that self-trigger, self-verify, and learn from past runs.
>
> **Trending:** Launched March 5, 2026. NVIDIA runs Cursor across 30,000+ engineers (3x code output). Rippling uses automations for incident triage and on-call handoffs.

## Quick Start Prompt

Use this prompt to design your first automation in Cursor:

```
You are a Cursor Automations architect. Help me set up an event-driven
AI agent for my codebase.

Context:
- Trigger type: [GitHub PR merged | Slack message | Linear issue created | Cron schedule | PagerDuty alert | Webhook]
- Repository: [your repo description]
- Goal: [e.g., "security review on every push to main", "auto-triage new bug reports", "weekly status digest"]

Design the automation:
1. **Trigger config** — What event, what filters (branch, label, channel)
2. **Agent instructions** — What the agent should do step-by-step
3. **Verification step** — How the agent checks its own work before posting
4. **Output action** — Where results go (Slack post, PR comment, Linear update, new issue)
5. **Memory rules** — What the agent should remember between runs to improve

Keep instructions specific and testable. Avoid vague directives.
Format as a ready-to-paste Cursor automation config.
```

## Example: Security Review on Push to Main

```
Trigger: Push to main branch
Instructions:
- Audit the diff for security vulnerabilities
- Skip issues already discussed in the PR thread
- Classify findings as Critical / High / Medium / Low
- Post only High+ findings to #security-alerts Slack channel
Verification: Re-read each finding and confirm it's not a false positive from test files
Memory: Track previously reported patterns to reduce duplicate alerts
```

## Common Automation Patterns

| Pattern | Trigger | Output |
|---------|---------|--------|
| Security audit | Push to main | Slack alert |
| PR quality review | PR opened | PR comment |
| Bug triage | Linear issue created | Label + assign |
| Status digest | Cron (weekly) | Slack summary |
| Incident response | PagerDuty alert | Runbook steps |

## Tips

- Start with ONE automation, verify it works, then expand
- Use the memory tool — agents get better over each run
- Set up isolated sandboxes so agents can't affect production
- Review agent outputs for the first week before trusting fully

---

> 🚀 **Want production-ready automation configs, multi-agent pipelines, cost optimization, and enterprise rollout playbooks?**
> Get the **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** — includes the complete Cursor Automations Production Pipeline with 6 ready-to-deploy configs.
