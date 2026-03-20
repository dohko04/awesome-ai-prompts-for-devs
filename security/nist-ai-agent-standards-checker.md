# NIST AI Agent Standards Compliance Checker (FREE)

> Evaluate your AI agent deployments against the NIST AI Agent Standards Initiative (March 2026). Covers security, interoperability, and governance requirements for autonomous AI systems.

## Why This Matters

NIST launched its AI Agent Standards Initiative to help companies safely adopt autonomous AI systems. If you're building agents that take actions (API calls, file access, purchases), compliance is shifting from optional to expected — especially for B2B and regulated industries.

## Quick Compliance Checklist

```yaml
# nist-agent-compliance.yaml — Score your agent deployment

nist_agent_standards_check:
  
  identity_and_authentication:
    - question: "Does every agent have a unique, verifiable identity?"
      check: "Agent IDs traceable in audit logs"
    - question: "Can you distinguish agent actions from human actions in logs?"
      check: "Separate auth tokens for agents vs humans"
    - question: "Do agents authenticate before accessing external services?"
      check: "Service-to-service auth (mTLS, OAuth2 client credentials)"
  
  action_boundaries:
    - question: "Are agent permissions explicitly defined and limited?"
      check: "Principle of least privilege applied"
    - question: "Can agents be stopped mid-execution?"
      check: "Kill switch / circuit breaker exists"
    - question: "Do destructive actions require human approval?"
      check: "Human-in-the-loop for delete, send, purchase, deploy"
  
  data_handling:
    - question: "Do agents access only the data they need?"
      check: "Data scoping per agent role"
    - question: "Is PII/PHI filtered before agent processing?"
      check: "Pre-processing pipeline strips sensitive data"
    - question: "Are agent conversations/contexts logged and auditable?"
      check: "Immutable audit trail with retention policy"
  
  interoperability:
    - question: "Do agents use standard protocols (MCP, A2A, OpenAPI)?"
      check: "No proprietary-only communication"
    - question: "Can agents from different vendors collaborate safely?"
      check: "Protocol-level trust boundaries"
    - question: "Is there a registry of agent capabilities?"
      check: "Service catalog or agent manifest file"
  
  incident_response:
    - question: "What happens when an agent misbehaves?"
      check: "Automated containment + alert pipeline"
    - question: "Can you roll back agent actions?"
      check: "Transaction log with undo capability"
    - question: "Is there a post-incident review process?"
      check: "RCA template specific to agent failures"

scoring:
  per_item: "YES=1, PARTIAL=0.5, NO=0"
  thresholds:
    excellent: ">= 12 / 15"
    acceptable: ">= 9 / 15"
    at_risk: "< 9 / 15"
```

## Agent Identity Template

```json
{
  "agent_id": "agent-billing-reconciler-001",
  "version": "1.2.0",
  "owner": "platform-team",
  "permissions": ["read:invoices", "read:payments", "write:reconciliation_log"],
  "denied_permissions": ["write:payments", "delete:*", "admin:*"],
  "max_actions_per_minute": 100,
  "human_approval_required": ["refund", "credit_adjustment"],
  "kill_switch_endpoint": "/api/agents/billing-reconciler/stop",
  "audit_log": "s3://audit-logs/agents/billing-reconciler/"
}
```

## Quick Risk Assessment

| Agent Type | Risk Level | NIST Focus Areas |
|-----------|-----------|-----------------|
| Read-only assistant | Low | Identity, data scoping |
| Internal automation | Medium | Permissions, audit trail |
| Customer-facing agent | High | All areas + incident response |
| Financial/healthcare agent | Critical | Full compliance + human-in-loop |

## Common Gaps

1. **No agent identity** — Agents share human API keys (can't distinguish who did what)
2. **Over-permissioned** — Agent has admin access "because it's easier"
3. **No kill switch** — Can't stop a runaway agent without killing the entire service
4. **No audit trail** — Agent actions not logged separately from application logs

---

> 🔒 **Want the full compliance pipeline?** The PRO version includes a Python compliance scanner, automated NIST mapping engine, CI/CD compliance gates, Grafana governance dashboard, and incident response playbook with agent-specific RCA templates.
>
> **[Get AI Dev Toolkit PRO — $9 USD](https://ai-dev-toolkit-five.vercel.app)**
