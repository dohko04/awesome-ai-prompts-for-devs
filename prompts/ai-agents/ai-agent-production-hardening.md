# 🚀 AI Agent Production Hardening Checklist

Take your AI agent from demo to production with a comprehensive hardening review. Covers reliability, cost control, observability, and failure recovery — the stuff that breaks at 3 AM.

## The Prompt

```
You are a senior AI/ML engineer who has deployed dozens of agent systems to production. I'm about to deploy an AI agent and need you to audit it for production readiness.

Here's my agent setup:
- **What it does:** {AGENT_DESCRIPTION}
- **Framework:** {FRAMEWORK: LangGraph | CrewAI | AutoGen | OpenAI Assistants | custom}
- **LLM provider:** {PROVIDER: OpenAI | Anthropic | Google | local}
- **Expected load:** {REQUESTS_PER_DAY}
- **Current stage:** {STAGE: prototype | staging | pre-prod}

Run through this production hardening checklist and give me specific, actionable fixes:

### 1. Reliability & Error Handling
- What happens when the LLM returns malformed output? Show me a retry + fallback pattern.
- What happens when a tool call fails mid-chain? Design a recovery strategy.
- Add timeout logic: max seconds per LLM call, max total agent run time.
- Define circuit breaker thresholds (e.g., 5 failures in 60s → stop calling).

### 2. Cost Control
- Estimate monthly cost at my expected load. Break down by: LLM tokens, tool calls, infra.
- Suggest a token budget per request with hard cutoff logic.
- Recommend caching strategy (semantic cache, exact match, or hybrid).
- When should I use a smaller/cheaper model vs the main model?

### 3. Observability & Debugging
- Design a structured logging schema for: agent steps, tool calls, LLM responses, latency.
- What metrics should I track? (success rate, avg tokens, p95 latency, cost per request)
- Recommend an observability stack (LangSmith, Langfuse, Helicone, or custom).
- Show me how to add trace IDs that follow a request through the entire agent chain.

### 4. Security & Guardrails
- Input validation: what should I sanitize before it hits the LLM?
- Output guardrails: how do I prevent hallucinated tool calls or data leaks?
- Rate limiting strategy per user/API key.
- PII detection and redaction approach.

### 5. Testing Strategy
- Unit tests for individual tools/functions.
- Integration tests for full agent flows (mock vs real LLM calls).
- Eval suite: how do I measure agent quality over time?
- Regression testing: catch when a model update breaks my agent.

### 6. Deployment & Scaling
- Recommend deployment pattern (serverless, container, queue-based).
- How to handle long-running agents (>30s) in serverless?
- Blue-green or canary deployment for agent updates.
- Database/state management for multi-turn conversations.

For each item, give me:
- ✅ What to implement (code snippet or config where possible)
- ⚠️ Common pitfall to avoid
- 📊 How to verify it's working

Output as a prioritized checklist I can work through in order.
```

## Example Usage

```
Agent: Customer support agent that reads tickets, queries internal docs via RAG, 
       drafts responses, and escalates complex issues to humans.
Framework: LangGraph
LLM: Anthropic Claude Sonnet
Load: ~2,000 requests/day
Stage: staging
```

## Tips

- Start with reliability and cost control — they'll bite you first.
- Don't skip observability. You can't fix what you can't see.
- Test with adversarial inputs early: prompt injection, edge cases, empty inputs.
- Set up alerts for cost spikes BEFORE launch, not after.

---

> 🚀 **Want the full production deployment kit?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes battle-tested agent configs, Docker templates, monitoring dashboards, and eval pipelines — everything you need to ship agents to prod with confidence.
