# NVIDIA OpenShell Agent Sandbox Setup (FREE)

> GTC 2026 Launch — Secure runtime for autonomous AI agents. OpenShell is the sandboxed execution layer inside NVIDIA's Agent Toolkit that NemoClaw uses to run always-on coding agents safely.

## Why This Matters (March 17, 2026)

NVIDIA launched OpenShell as part of NemoClaw at GTC 2026. It's an open-source secure runtime that:
- Sandboxes autonomous agent execution (file system, network, processes)
- Works with OpenClaw, LangChain, CrewAI, and any agent framework
- Enables "always-on" agents without risking host system compromise
- Single-command setup via NemoClaw stack

## Quick Start Prompt

```
You are an AI agent security architect. Help me set up NVIDIA OpenShell
as a secure sandbox for my autonomous coding agents.

My setup:
- Agent framework: [OpenClaw/LangChain/CrewAI/custom]
- Host OS: [Ubuntu 22.04/24.04/macOS]
- Use case: [coding agent/data pipeline/devops automation]

Create a setup plan covering:

1. **OpenShell Installation**
   - Prerequisites check (Docker, NVIDIA Container Toolkit)
   - Single-command NemoClaw install
   - Verify sandbox isolation

2. **Security Configuration**
   - File system: whitelist only project directories
   - Network: allow only required endpoints (git, npm, pip)
   - Process: limit CPU/memory per agent session
   - Secrets: mount read-only credential volumes

3. **Agent Integration**
   - Connect my [framework] agent to OpenShell runtime
   - Configure tool permissions (shell, browser, file access)
   - Set up logging for audit trail

4. **Quick Validation**
   - Test: agent can read/write project files ✓
   - Test: agent CANNOT access host system files ✓
   - Test: agent CANNOT make unauthorized network calls ✓
   - Test: resource limits enforced ✓

Output a working docker-compose.yml and setup script.
```

## What You Get

- Basic sandbox setup for 1 agent
- Core security rules (filesystem + network)
- Simple validation checklist

## Want Production-Grade Agent Security?

The **PRO version** includes:
- 🔒 Multi-agent isolation (each agent in its own sandbox with different permissions)
- 📊 Real-time resource monitoring with Grafana dashboards
- 🔄 Auto-scaling sandbox pools for team environments
- 🛡️ Enterprise compliance configs (SOC2, HIPAA data handling)
- 💰 Cost calculator for sandbox compute overhead
- 📋 Full Kubernetes manifests for production deployment

**Get the complete OpenShell Production Pipeline → [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 196+ pro resources for $9**

---

*Part of the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) by Dohko — Built during a mass layoff, now helping devs survive the AI shift.*
