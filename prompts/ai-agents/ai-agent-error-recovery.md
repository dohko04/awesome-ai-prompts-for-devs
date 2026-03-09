# 🔄 AI Agent Error Recovery & Self-Healing Patterns

> **Category:** AI Agents · **Works with:** Claude, ChatGPT, Gemini  
> **Trending:** March 2026 — As AI agents go production, error recovery is the #1 reliability gap

## The Prompt

```
You are an expert AI agent reliability engineer. Design a comprehensive error recovery and self-healing system for my AI agent application.

**My Agent Stack:**
- Runtime: [e.g., Node.js / Python]
- Framework: [e.g., LangGraph / CrewAI / custom]
- LLM Provider: [e.g., Anthropic Claude / OpenAI / mixed]
- Tools: [list the tools your agent uses]
- State Management: [e.g., in-memory / Redis / database]

## Design These Recovery Patterns:

### 1. LLM Call Failures
- Retry with exponential backoff + jitter
- Automatic model fallback chain (e.g., Opus → Sonnet → Haiku)
- Request hedging for critical paths
- Token budget exceeded → automatic context compression

### 2. Tool Execution Failures  
- Tool timeout handling with configurable limits
- Partial result recovery (don't lose work done so far)
- Alternative tool routing (if tool A fails, try tool B)
- Human-in-the-loop escalation triggers

### 3. State Corruption Recovery
- Checkpoint system: save agent state every N steps
- Rollback mechanism to last known good state
- Idempotent action design (safe to retry)
- Dead letter queue for unprocessable tasks

### 4. Infinite Loop Prevention
- Max iteration guards per agent/task
- Cost ceiling per execution ($X max spend)
- Divergence detection (agent repeating same actions)
- Circuit breaker pattern for cascading failures

### 5. Observability
- Structured logging for every decision point
- Trace ID propagation across agent handoffs
- Cost tracking per agent run
- Alert thresholds for anomalous behavior

For each pattern, provide:
- TypeScript/Python implementation code
- When to use vs. when it's overkill
- Real failure scenarios it prevents
```

## Example Output

The AI will generate production-ready error handling like:

```typescript
// Model fallback chain with automatic retry
class ResilientLLMClient {
  private models = ['claude-opus-4', 'claude-sonnet-4', 'claude-haiku-3'];
  
  async complete(prompt: string, opts?: CompletionOpts): Promise<string> {
    for (const model of this.models) {
      try {
        return await this.callWithRetry(model, prompt, opts);
      } catch (e) {
        logger.warn(`Model ${model} failed, falling back...`, { error: e });
        continue;
      }
    }
    throw new AgentError('All models exhausted', { escalate: true });
  }
}
```

## Why This Matters (March 2026)

With AI agents moving from demos to production, the #1 complaint from engineering teams is **reliability**. The "happy path" works great — it's the error cases that kill you. This prompt gives you battle-tested patterns used by teams running agents at scale.

## Use Cases

- Production AI agent deployments
- Multi-agent orchestration systems
- Autonomous coding pipelines
- Customer-facing AI workflows

---

> 💡 **Want the complete production agent toolkit?** This is a simplified version. The full [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes ready-to-deploy agent templates with built-in error recovery, observability dashboards, and cost management — all battle-tested patterns in one package.
