# 🔒 Teleport Beams: Agent Runtime Security Starter

> Secure your AI agents in production with isolated runtimes, zero-secret identity, and audit trails. Based on Teleport Beams (launched March 19, 2026).

## The Problem

Most teams run AI agents with:
- ❌ Shared API keys in environment variables
- ❌ No isolation between agent and host system
- ❌ No audit trail of agent actions
- ❌ Each team building their own container/VM setup from scratch

## Quick Threat Assessment

Ask these questions about each AI agent you run:

```yaml
# agent-security-checklist.yaml
# Score: 1 point per YES answer. 5+ = HIGH RISK

agent_name: "your-coding-agent"

questions:
  - "Does this agent use shared credentials (API keys, tokens)?"     # YES/NO
  - "Can this agent access services beyond what it needs?"            # YES/NO
  - "Is there no log of what this agent accesses?"                    # YES/NO
  - "Does this agent run in the same environment as production?"      # YES/NO
  - "Could a compromised agent move laterally to other services?"     # YES/NO
  - "Are agent credentials long-lived (>24h)?"                        # YES/NO
  - "Is there no way to instantly revoke agent access?"               # YES/NO

# Score interpretation:
# 0-2: Low risk — you have basic controls
# 3-4: Medium risk — gaps that need attention
# 5-7: HIGH risk — your agents are a breach waiting to happen
```

## Basic Agent Isolation Config

```yaml
# agent-runtime-config.yaml
# Minimum viable secure agent runtime

agent_runtimes:
  coding_agent:
    isolation: "container"  # container | vm | firecracker
    network:
      default: "deny-all"
      allowed:
        - host: "api.github.com"
          port: 443
        - host: "staging.internal"
          port: 443
    identity:
      type: "short-lived-certificate"  # NOT api-key
      ttl: "1h"
      auto_rotate: true
    audit:
      log_all_actions: true
      log_network: true
      retention: "90d"
    limits:
      max_lifetime: "2h"
      max_memory: "2GB"
      max_cpu: 2
```

## Zero-Secret Checklist

Before deploying any AI agent to production:

- [ ] No API keys in environment variables
- [ ] No secrets in config files
- [ ] Agent uses short-lived certificates (not tokens)
- [ ] Network policy is deny-all + explicit allowlist
- [ ] All agent actions are logged
- [ ] Agent can be killed/revoked instantly
- [ ] Agent runtime is isolated (container/VM minimum)

---

## 🔥 Want the Full Pipeline?

This starter covers the basics. The **PRO version** includes:

- **Firecracker VM Fleet Manager** — Python tool to configure and manage isolated agent runtimes at scale
- **Zero-Secret Identity Architecture** — Complete SPIFFE/SPIRE + Teleport integration with migration checklist
- **Agent Audit & Compliance Dashboard** — SOC2/ISO27001 automated reporting with risk scoring per agent
- **CI/CD Security Gates** — GitHub Actions workflow that blocks insecure agent deployments
- **Grafana Monitoring Dashboard** — Real-time agent action monitoring with anomaly detection

**Get it →** [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) — 230+ production-ready AI engineering resources
