# Stripe Machine Payments Protocol (MPP) — Agentic Commerce Starter

> Build AI agents that make autonomous payments via Stripe's Machine Payments Protocol.
> Trending: March 18-20, 2026 — Stripe + Visa launched agentic commerce infrastructure.

## Basic MPP Agent Payment Integration

```typescript
// mpp-agent-payment-basic.ts — Simple agent payment with safety limits

interface AgentPaymentConfig {
  agentId: string;
  maxTransactionUsd: number;
  dailyBudgetUsd: number;
}

class BasicMPPAgent {
  private dailySpend = 0;

  constructor(
    private stripe: any, // Stripe instance
    private config: AgentPaymentConfig
  ) {}

  async pay(merchantId: string, amountCents: number, description: string) {
    // Safety: check limits
    if (amountCents > this.config.maxTransactionUsd * 100) {
      throw new Error(`Exceeds max transaction: $${this.config.maxTransactionUsd}`);
    }
    if (this.dailySpend + amountCents > this.config.dailyBudgetUsd * 100) {
      throw new Error(`Exceeds daily budget: $${this.config.dailyBudgetUsd}`);
    }

    const payment = await this.stripe.paymentIntents.create({
      amount: amountCents,
      currency: 'usd',
      metadata: {
        agent_id: this.config.agentId,
        merchant_id: merchantId,
        protocol: 'mpp_v1',
      },
      description: `[MPP Agent] ${description}`,
    });

    this.dailySpend += amountCents;
    return { transactionId: payment.id, amount: amountCents };
  }

  getSpend() { return this.dailySpend / 100; }
}

// Usage
const agent = new BasicMPPAgent(stripe, {
  agentId: 'my-research-agent',
  maxTransactionUsd: 10,
  dailyBudgetUsd: 50,
});

await agent.pay('api-provider', 500, 'API access — 1000 queries');
```

## Key Safety Rules for Agent Payments

1. **Always set budget limits** — daily, weekly, per-transaction
2. **Merchant allowlists** — only let agents pay approved services
3. **Human approval gates** — require approval above threshold amounts
4. **Anomaly detection** — flag transactions that deviate from patterns
5. **Audit logging** — log every transaction for compliance

---

**Want the full pipeline?** The PRO version includes:
- Multi-agent budget governor with anomaly detection
- Agent-to-agent service marketplace template
- Grafana payment monitoring dashboard
- CI/CD payment policy enforcement

👉 **[AI Dev Toolkit — 266 Pro Resources, $9 USD](https://ai-dev-toolkit-five.vercel.app)**
