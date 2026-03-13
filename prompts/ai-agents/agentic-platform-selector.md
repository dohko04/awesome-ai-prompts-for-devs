# Agentic AI Platform Selector (FREE)

> March 2026 has seen an explosion of agentic AI platforms — from CrewAI and LangGraph to Kore.ai Agent Studio and Google Antigravity. This prompt helps you pick the right one for your use case.

## The Prompt

```
You are an AI engineering consultant helping me choose the right agentic AI platform for my project.

**My requirements:**
- Use case: [DESCRIBE - e.g., "customer support automation", "code review pipeline", "data processing"]
- Team size: [solo dev / small team / enterprise]
- Budget: [free/open-source only / <$100/mo / enterprise budget]
- Deployment: [local / cloud / hybrid]
- Must-haves: [e.g., "multi-agent coordination", "human-in-the-loop", "tool use"]

**Evaluate these platforms against my requirements:**

1. **CrewAI** — Role-based agents, Python-native, open-source
2. **LangGraph** — Graph-based workflows, LangChain ecosystem
3. **Google Antigravity** — Multi-agent IDE with Manager View
4. **OpenAI Assistants API** — Managed, tool use, code interpreter
5. **Claude Agent Teams** — Native Opus 4.6 multi-agent
6. **Kore.ai Agent Studio** — Enterprise low-code/pro-code

For each, rate (1-5): ease of setup, scalability, cost efficiency, community/docs, production-readiness.

**Output:** Recommendation with reasoning, migration path if I outgrow it, and a "start here" code snippet for the winner.
```

## Quick Decision Matrix

| If you need... | Start with... |
|---|---|
| Quick prototype, solo dev | CrewAI |
| Complex workflows, state machines | LangGraph |
| Enterprise compliance + support | Kore.ai |
| Multi-agent coding | Google Antigravity or Claude Agent Teams |
| Managed infra, minimal ops | OpenAI Assistants API |

---

> 🔥 **Want the full evaluation framework?** The PRO version includes: 15-criteria scoring matrix, production deployment checklist for each platform, cost modeling calculator (tokens × agents × calls), migration playbooks between platforms, and real benchmark data.
>
> **[Get the AI Dev Toolkit — 127+ pro resources for $9](https://ai-dev-toolkit-five.vercel.app)**
