# Rogue AI Agent Containment Starter

> After Meta's rogue AI agent exposed sensitive data (March 2026), every team needs agent containment. Use this starter to define permission boundaries for your AI agents.

## Quick Permission Boundary Template

```yaml
# agent-permissions.yaml
# Define what your AI agents CAN and CANNOT do

agents:
  your_agent_name:
    role: "Describe what this agent does"
    permissions:
      read:
        - "source_code:*"        # What it can read
        - "pull_requests:*"
      write:
        - "pr_comments:create"   # What it can write (be specific!)
      deny:                       # ALWAYS define denials
        - "production_data:*"    # Never production
        - "user_data:*"          # Never PII
        - "secrets:*"            # Never credentials
        - "infrastructure:*"     # Never infra changes
    
    safety:
      max_actions_per_minute: 10  # Rate limit
      session_timeout: "30m"      # Auto-expire
      requires_human_approval:    # Manual gate for risky actions
        - "deploy_to_staging"
        - "send_external_message"

# Lessons from Meta's incident:
# 1. The agent gave incorrect advice that led to unauthorized data access
# 2. Exposure lasted ~2 hours before detection
# 3. No permission boundaries would have caught it in seconds
```

## Agent Security Checklist

```markdown
For EVERY AI agent you deploy, verify:

- [ ] Deny list covers: PII, secrets, production data, infrastructure
- [ ] Rate limit is set (recommended: 10-30 actions/minute)
- [ ] Session timeout exists (recommended: 30min-2h)
- [ ] Write permissions are specific (no wildcards like "database:*")
- [ ] Human approval required for: deploys, external comms, data exports
- [ ] Audit logging enabled for all actions
- [ ] Circuit breaker configured (auto-stop after N failures)
- [ ] Agent cannot modify its own permissions
- [ ] Agent cannot grant access to other agents
```

## Blast Radius Quick Assessment

```
Score your agent (add points):
+30 = Can access PII or user data
+25 = Can write to production
+20 = Can modify databases
+15 = Can send external communications
+15 = Can change infrastructure
+10 = No rate limit configured
───────────────────────────────
0-20  = LOW risk (review quarterly)
20-40 = MEDIUM (add monitoring)
40-60 = HIGH (add circuit breakers + approvals)
60+   = CRITICAL (needs human-in-the-loop for ALL actions)

Meta's rogue agent scored ~85. Don't be Meta.
```

---

> 💡 **Want the full containment pipeline?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes the complete Rogue Agent Containment Pipeline PRO with:
> - Runtime Containment Engine (Python, 5-layer enforcement)
> - Blast Radius Calculator with Meta incident comparison
> - Incident Response Playbook (P0-P2 severity levels)
> - Automated Daily Agent Audit Script (CI/CD ready)
> - Permission drift detection between config versions
