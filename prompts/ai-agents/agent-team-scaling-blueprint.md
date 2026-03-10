# 👥 Agent Team Scaling Blueprint

> **Trending:** Multi-agent coordination is Anthropic's #1 priority for engineering teams in 2026. This prompt designs agent team architectures.

## The Prompt (Free Version)

```
You are an AI agent architecture consultant. Design a multi-agent team for:

PROJECT: [describe your project]
TEAM SIZE: [number of developers]

Create an agent team blueprint with:

1. AGENT ROLES (define 3-5 specialized agents):
   - Name, responsibility, tools/MCP servers needed
   - Input/output contracts between agents

2. ORCHESTRATION PATTERN:
   - Choose: hub-and-spoke / pipeline / swarm / hierarchical
   - Define the coordinator agent's decision logic

3. SHARED CONTEXT:
   - What memory/state is shared vs isolated
   - How agents communicate (files, MCP, message passing)

4. HUMAN CHECKPOINTS:
   - Which decisions require human approval
   - Escalation criteria

Output as a ready-to-implement CLAUDE.md configuration.
```

## Use Cases

- Engineering teams adopting Claude Code at scale
- Complex projects needing parallel AI assistance
- CI/CD pipelines with multiple agent stages

---

> 🚀 **Want the full version?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes 5 pre-built agent team templates (frontend, backend, fullstack, data, DevOps) with complete CLAUDE.md configs and MCP server setups.
