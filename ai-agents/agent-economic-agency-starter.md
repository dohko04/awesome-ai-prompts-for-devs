# AI Agent Economic Agency Starter

> 💰 Build AI agents that safely execute trades, manage budgets, and negotiate contracts with comprehension-gated guardrails

## When to Use
- Building agents that handle financial transactions
- Deploying AI for budget management or procurement
- Creating trading bots with safety constraints
- Any agent that spawns sub-agents with economic authority

## Quick Start Prompt

```
You are an AI Agent Economy Architect specializing in safe economic agency.

CONTEXT: As AI agents gain economic capabilities (executing trades, managing
budgets, negotiating contracts, spawning sub-agents), the key challenge is
ensuring agents truly "comprehend" their economic actions before executing.
The Comprehension-Gated architecture ensures no agent acts beyond its
verified understanding.

TASK: Help me design an economically-capable agent system:

1. **Comprehension Gates**
   - Pre-action verification: Does the agent understand the economic impact?
   - Confidence thresholds per transaction tier
   - Escalation rules when comprehension score is low

2. **Budget Architecture**
   - Hierarchical spending limits (agent → sub-agent → sub-sub-agent)
   - Real-time budget tracking and alerts
   - Automatic circuit breakers at configurable thresholds

3. **Transaction Safety**
   - Multi-signature requirements for high-value actions
   - Reversibility windows for non-critical transactions
   - Audit trail with full decision reasoning

4. **Sub-Agent Spawning**
   - Budget inheritance rules
   - Authority delegation limits
   - Termination triggers for runaway spending

OUTPUT FORMAT:
- Agent hierarchy diagram
- Budget config YAML
- 3 comprehension gate examples
- Safety checklist

MY USE CASE: [describe what economic actions your agents need]
MAX BUDGET: [total budget agents can manage]
RISK TOLERANCE: [low/medium/high]
```

## Example Architectures
- **E-commerce Agent**: Manages ad spend, negotiates supplier pricing, tracks ROI
- **Trading Bot**: Executes trades within strict comprehension-gated limits
- **Procurement Agent**: Compares vendors, negotiates contracts, manages POs

## Safety Principles
- No agent should execute transactions it can't explain
- Budget limits must cascade down the agent hierarchy
- All economic actions must be reversible within a configurable window
- Human approval required above configurable thresholds

---

> 💡 **Want the full production pipeline?** The PRO version includes multi-tier budget YAML configs, comprehension scoring engine, transaction audit dashboard, sub-agent governance framework, and cost optimization models → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
