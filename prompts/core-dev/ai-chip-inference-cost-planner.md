# AI Chip & Inference Cost Planner

> **FREE starter** — Plan your AI inference strategy based on the 2026 chip investment landscape (Samsung $73B, NVIDIA Vera Rubin, AMD MI400). Choose the right hardware tier for your workloads and budget.

## The Prompt

```
You are an AI infrastructure cost strategist who tracks the semiconductor landscape.

I need to plan my inference infrastructure based on current chip economics.

My situation:
- Monthly AI API spend: $[amount]
- Primary workloads: [coding agents / RAG / chat / batch processing / fine-tuning]
- Team size: [number] developers
- Current providers: [OpenAI / Anthropic / Google / self-hosted]
- Latency requirement: [real-time < 200ms / interactive < 2s / batch — any]

Analyze and recommend:

1. **Chip Landscape Impact Assessment**
   - How Samsung HBM4 investment affects GPU memory costs (12-18 month outlook)
   - NVIDIA vs AMD vs custom silicon price trajectory
   - When self-hosting breaks even vs API (show the math)

2. **Provider Cost Optimization**
   - Compare: OpenAI GPT-5.4 mini ($0.75/1M in) vs Claude Sonnet 4.6 vs Gemini 2.5 Flash
   - For my workload mix, which provider minimizes cost at my quality bar?
   - Multi-provider routing: which requests go where?

3. **Hardware Tier Selector**
   Based on my workloads, recommend:
   | Tier | Hardware | Use Case | Monthly Cost | When to Use |
   
   Tiers: Cloud API → Managed GPU (Lambda/CoreWeave) → Self-hosted (DGX Spark) → Edge (Jetson/NPU)

4. **12-Month Cost Projection**
   - Current trajectory vs optimized strategy
   - Expected savings from chip competition driving prices down
   - Migration triggers (when to switch tiers)

Output a concrete monthly budget breakdown with action items.
```

## When to Use

- Quarterly infrastructure budget planning
- Before scaling AI agent deployments
- When evaluating self-hosting vs cloud API

## What You Get (Free vs Pro)

| Feature | Free (This) | Pro |
|---------|------------|-----|
| Cost planning prompt | ✅ | ✅ |
| Python cost calculator script | ❌ | ✅ Multi-provider |
| Real-time price tracker | ❌ | ✅ API monitors |
| Migration decision engine | ❌ | ✅ Auto-triggers |
| Grafana cost dashboard | ❌ | ✅ JSON template |
| Team budget allocation | ❌ | ✅ Per-dev tracking |

---

**💰 Want the full AI Chip & Inference Cost Pipeline?** Get the production version with automated cost tracking, migration decision engine, and Grafana dashboards → [AI Dev Toolkit Pro](https://ai-dev-toolkit-five.vercel.app)
