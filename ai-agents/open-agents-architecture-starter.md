# Open Agents Architecture — Starter Guide

> **Build with the open agents paradigm: open models + open orchestration + open tool interfaces.**
> Based on NVIDIA GTC 2026 closing panel (March 18-20): the industry shift from "open models" to "open agents."
>
> 🔗 **[Get the full Open Agents Production Pipeline →](https://ai-dev-toolkit-five.vercel.app)**
> Includes: multi-framework orchestrator, model-agnostic agent patterns, NIM + open-weight routing, security architecture, and vendor independence playbook.

---

## The Open Agents Shift

GTC 2026 made it clear: the market isn't split between "proprietary vs open models" anymore. The real shift is **open agents** — systems where models, tools, memory, and orchestration are all interchangeable.

**Key principles:**
1. **Model-agnostic agents** — swap Nemotron, Mistral, Qwen, Llama without rewriting
2. **Open tool interfaces** — MCP, A2A, AG-UI as standard protocols
3. **Open orchestration** — NemoClaw, LangGraph, CrewAI, OpenClaw interop
4. **Open memory** — shared context across agent frameworks

## Starter Architecture

```yaml
# open-agent-config.yaml
agent:
  name: "my-open-agent"
  framework: "langraph"  # or crewai, nemoclaw, openclaw

  models:
    primary: "nemotron-4-340b"    # NVIDIA NIM
    fallback: "mistral-small-4"   # Self-hosted
    fast: "qwen-3.5-7b"          # Local/edge

  tools:
    protocol: "mcp"
    servers:
      - name: "filesystem"
        transport: "stdio"
      - name: "github"
        transport: "sse"
        url: "http://localhost:3001"

  memory:
    backend: "openviking"  # or chroma, pgvector
    shared: true           # cross-agent access

  routing:
    strategy: "cost-aware"
    max_cost_per_task: 0.10
```

## Quick Start Prompt

```
You are designing an open-agent system. The user's requirements:

REQUIREMENTS: {{describe_what_agents_should_do}}

Design an agent architecture following open agent principles:
1. MODEL LAYER: Choose 2-3 open-weight models (primary + fallback + fast)
   - Consider: Nemotron 4, Mistral Small 4, Qwen 3.5, Llama 4
2. TOOL LAYER: Define MCP servers needed
3. ORCHESTRATION: Pick framework (LangGraph/CrewAI/NemoClaw)
4. MEMORY: Shared vector store + conversation history
5. ROUTING: Cost-aware model selection per task type

Output a YAML config + architecture diagram (ASCII).
Explain trade-offs for each choice.
```

## Open vs Proprietary Agent Comparison

| Dimension | Open Agents | Proprietary Agents |
|-----------|-------------|-------------------|
| Model lock-in | None — swap freely | High — API-dependent |
| Cost control | Self-host option | Pay-per-token only |
| Data privacy | On-prem possible | Data leaves your infra |
| Customization | Fine-tune freely | Prompt engineering only |
| Support | Community + vendors | Single vendor SLA |

---

> 💡 **Want the full production pipeline?** The PRO version includes a multi-framework orchestrator with automatic failover, NIM container fleet management, security architecture with RBAC, vendor independence migration scripts, and cost optimization across 10+ providers.
>
> **[→ Get AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)**
