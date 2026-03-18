# Gartner Guardian Agent — Zero-Trust AI Agent Identity Setup

> **Trend:** Gartner's new "Guardian Agents" market category (March 2026) defines AI agents that manage identities and access for other AI agents with zero-trust policies. Orchid Security, 1Password Unified Access, and Reco AI Agent Security are all racing to own this space.

## What This Does

Gives you a starter framework for implementing zero-trust identity governance for your AI agents — the pattern Gartner now calls "Guardian Agents."

## Quick Start: Guardian Agent Policy

```yaml
# guardian-agent-policy.yaml
# Zero-trust identity governance for AI agents

agent_identity:
  registration:
    require_purpose_declaration: true
    max_credential_ttl: "1h"
    rotation_policy: "on-every-session"
  
  authentication:
    method: "mTLS + JWT"
    token_scope: "least-privilege"
    require_human_approval_for:
      - "database_write"
      - "external_api_call"
      - "file_system_delete"
      - "credential_access"

  access_tiers:
    read_only:
      description: "Agent can read data, no mutations"
      auto_approve: true
      audit_level: "standard"
    
    write_limited:
      description: "Agent can write to pre-approved resources"
      auto_approve: false
      require_justification: true
      audit_level: "enhanced"
    
    admin:
      description: "Full access — human-in-the-loop required"
      auto_approve: false
      require_human_approval: true
      audit_level: "forensic"
      max_session_duration: "15m"

audit:
  log_all_agent_actions: true
  anomaly_detection:
    baseline_window: "7d"
    alert_on_deviation: 2.0  # standard deviations
  retention: "90d"
```

## Agent Identity Checker Script

```bash
#!/bin/bash
# guardian-agent-audit.sh — Quick audit of AI agent access patterns

echo "🛡️ Guardian Agent Audit"
echo "======================"

# Check for hardcoded credentials in agent configs
echo ""
echo "1. Scanning for hardcoded credentials..."
grep -rn "api_key\|secret\|password\|token" \
  --include="*.yaml" --include="*.yml" --include="*.json" --include="*.env" \
  . 2>/dev/null | grep -v node_modules | grep -v ".git" | head -20

if [ $? -eq 0 ]; then
  echo "⚠️  FOUND hardcoded credentials — migrate to secret manager"
else
  echo "✅ No hardcoded credentials found"
fi

# Check for agents with no TTL
echo ""
echo "2. Checking for persistent agent sessions..."
grep -rn "ttl.*-1\|ttl.*never\|no_expiry\|persistent.*true" \
  --include="*.yaml" --include="*.yml" --include="*.json" \
  . 2>/dev/null | grep -v node_modules | grep -v ".git"

echo ""
echo "3. Agent access summary:"
echo "   - Total agent configs found: $(find . -name 'agent*.yaml' -o -name 'agent*.yml' -o -name 'agent*.json' 2>/dev/null | wc -l)"
echo "   - Configs with audit enabled: $(grep -rl 'audit.*true\|logging.*true' --include='*.yaml' --include='*.yml' . 2>/dev/null | wc -l)"

echo ""
echo "📋 Recommendation: Implement Guardian Agent pattern"
echo "   → Every agent gets scoped, short-lived credentials"
echo "   → Every action is audited"
echo "   → Sensitive ops require human approval"
```

## Key Principles (Gartner Guardian Agent Pattern)

1. **Every agent is an identity** — not a shared service account
2. **Least-privilege by default** — agents request access, don't assume it
3. **Short-lived credentials** — rotate on every session, max 1h TTL
4. **Audit everything** — log every agent action, detect anomalies
5. **Human-in-the-loop** — sensitive operations need human approval

---

> 🔥 **Want the full Guardian Agent Pipeline?** The PRO version includes: Python identity manager with mTLS, multi-framework agent registration (LangChain/CrewAI/OpenClaw), compliance mapping (SOC2/HIPAA/GDPR), Grafana anomaly dashboard, and team rollout playbook.
>
> **Get it at: https://ai-dev-toolkit-five.vercel.app**
