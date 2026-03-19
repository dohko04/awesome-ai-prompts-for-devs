# ServiceNow AI Gateway — Agent Governance Starter

> Enterprise AI agent catalog and governance setup for ServiceNow's March 2026 AI Gateway release. Auto-discovery, model routing, and compliance in one config.

## When to Use

- Your org runs multiple AI agents across departments
- You need a central catalog of all AI models and agents in production
- Compliance requires audit trails for every AI decision
- You want auto-discovery of shadow AI usage

## Quick Assessment Checklist

```yaml
# servicenow-ai-gateway-readiness.yaml
organization:
  current_ai_agents: []  # List all known agents
  shadow_ai_risk: "high|medium|low"
  compliance_requirements:
    - SOC2
    - GDPR
    - HIPAA  # if applicable

gateway_readiness:
  servicenow_instance: ""  # your-instance.service-now.com
  ai_agent_studio_enabled: false
  existing_model_providers:
    - name: "openai"
      models_in_use: ["gpt-5.4", "gpt-5.4-mini"]
      monthly_spend_usd: 0
    - name: "anthropic"
      models_in_use: ["claude-opus-4.6"]
      monthly_spend_usd: 0

governance_gaps:
  centralized_catalog: false
  cost_attribution: false
  usage_audit_trail: false
  model_approval_workflow: false
```

## Starter Governance Policy

```markdown
## AI Agent Governance Policy (Template)

### 1. Registration
- ALL AI agents must be registered in the AI Gateway catalog
- Auto-discovered agents have 7 days to complete registration
- Unregistered agents will be blocked after grace period

### 2. Model Approval
- Tier 1 (pre-approved): GPT-5.4, Claude Opus 4.6, Gemini Ultra
- Tier 2 (team-lead approval): Open-weight models (Nemotron, Llama)
- Tier 3 (CISO approval): Self-hosted, fine-tuned, or unknown models

### 3. Cost Controls
- Per-agent monthly budget caps
- Alert at 80% threshold
- Auto-throttle at 100%

### 4. Audit
- All prompts and responses logged for 90 days
- PII auto-redacted before logging
- Quarterly compliance review
```

## What You Get in the PRO Version

The **ServiceNow AI Gateway Production Pipeline** includes:
- Python auto-discovery scanner (finds all AI API calls in your codebase)
- Multi-provider catalog generator with cost attribution
- Compliance mapping engine (SOC2/HIPAA/GDPR controls → Gateway policies)
- Grafana monitoring dashboard for agent health and spend
- Team rollout playbook (30-day implementation plan)

---

🔗 **Get the full pipeline:** [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 240+ production-ready AI/dev resources for $9.
