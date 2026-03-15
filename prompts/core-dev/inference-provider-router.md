# 🔀 Inference Provider Router — Multi-Provider Strategy

> NVIDIA spent $20B acquiring Groq. Cerebras powers OpenAI Codex. The inference market is fragmenting. If you're locked into one provider, you're overpaying 3-10x on specific workloads. Use this prompt to build your multi-provider strategy.

## The Prompt

```markdown
You are an AI inference cost optimization consultant. I need help building a multi-provider inference strategy.

## My Current Setup
- **Primary provider:** [OpenAI / Anthropic / Google / Groq / local / other]
- **Models used:** [list models]
- **Monthly spend:** $[amount] (or estimate)
- **Main workloads:**
  1. [workload 1] — [requests/day] — latency need: [real-time / <2s / batch]
  2. [workload 2] — [requests/day] — latency need: [real-time / <2s / batch]
  3. [workload 3] — [requests/day] — latency need: [real-time / <2s / batch]

## Analyze and recommend:

### 1. Provider-Workload Matching
For each workload, recommend the optimal provider:
- Provider name + model
- Why it's better than my current choice
- Estimated cost per 1K requests
- Latency expectation (P50/P99)

### 2. Quick Wins (implement in 1 day)
List 3 optimizations I can do TODAY:
- Model downsizing opportunities (where a cheaper model is ≥95% as good)
- Caching opportunities (repeated prompts, similar queries)
- Batch API opportunities (non-real-time workloads at 50% cost)

### 3. Savings Estimate
```
Current monthly: $___
After optimization: $___
Savings: $___  (___%)
Effort to implement: ___ days
```

### 4. Failover Strategy
If my primary provider goes down, what's my fallback chain?

Be specific with numbers. I want actionable recommendations, not generic advice.
```

## Example Output

Generates a provider matrix with specific cost comparisons, quick-win optimizations, and a failover chain for your exact workloads.

## When to Use

- Monthly inference bill exceeding $50
- Evaluating new providers (Groq, Cerebras, NVIDIA NIM)
- Building production AI applications that need reliability
- Post-GTC 2026 when new inference options launch

## Pro Tip

The biggest savings usually come from **model downsizing** (using a 7B model for simple tasks instead of a frontier model) and **caching** (30-50% of requests in typical apps have similar prompts).

---

> 🔒 **Want the complete Inference Router?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) PRO version includes: production Python router with circuit breakers, cost tracking, auto-failover across 7 providers, Grafana dashboard configs, provider migration checklist with shadow testing, and batch optimization pipeline. **162 production-ready resources for $9 →** [ai-dev-toolkit-five.vercel.app](https://ai-dev-toolkit-five.vercel.app)
