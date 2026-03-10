# 🔍 AI Agent Observability & Tracing Setup

> Set up production-grade observability for your AI agents. Track token usage, latency, error rates, and reasoning quality across multi-agent workflows.

## The Prompt (Free Version)

```
You are an LLMOps Observability Engineer. Help me set up comprehensive tracing and monitoring for my AI agent system.

MY AGENT SETUP:
- Framework: {CrewAI/LangGraph/AutoGen/custom}
- Models used: {list_models}
- Number of agents: {count}
- Deployment: {local/cloud/hybrid}
- Current observability: {none/basic_logging/other}

TASK — Design my agent observability stack:

1. TRACING LAYER:
   - Instrument each agent call with trace IDs
   - Track: input tokens, output tokens, latency, model used
   - Capture parent-child relationships in multi-agent chains
   - Tool: recommend Langfuse, Arize Phoenix, or OpenTelemetry-based

2. KEY METRICS TO TRACK:
   - Token cost per task (broken down by agent)
   - Latency P50/P95/P99 per agent step
   - Error rate and retry count
   - Tool call success/failure rates
   - Reasoning quality score (if using evals)

3. ALERTING:
   - Cost spike detection (>2x normal for a task)
   - Latency degradation alerts
   - Agent loop detection (stuck in retry cycles)
   - Token budget exhaustion warnings

4. DASHBOARD:
   - Give me a Grafana/dashboard config or describe panels needed
   - Daily cost breakdown by agent/task
   - Success rate trends
   - Model comparison metrics

Provide implementation code snippets for my framework.
```

## When to Use
- When running AI agents in production
- When your LLM costs are unpredictable
- When debugging multi-agent workflows feels like guessing
- When you need to justify AI spend to stakeholders

## Why This Matters (March 2026)
Multi-agent systems are going to production everywhere, but most teams fly blind. Without observability, a single misconfigured agent can burn through your API budget in minutes. LLMOps observability is the "DevOps monitoring" moment for AI — essential, not optional.

---

> 💡 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes ready-to-deploy observability configs for CrewAI, LangGraph, and custom agents — plus Langfuse integration templates, cost alerting scripts, and a pre-built Grafana dashboard JSON.
