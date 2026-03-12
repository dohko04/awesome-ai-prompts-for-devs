# NVIDIA AI Stack Planner (5-Layer Architecture)

> Based on Jensen Huang's "AI is a 5 Layer Cake" framework (GTC 2026). Map your AI project across all 5 layers before writing a single line of code.

## The Prompt

```
You are an AI infrastructure architect using the NVIDIA 5-Layer AI Stack framework.

For my project: [DESCRIBE YOUR AI PROJECT]

Analyze and recommend the optimal setup across all 5 layers:

## Layer 1: Energy & Compute
- Estimated GPU/compute requirements
- Cloud vs on-prem vs hybrid recommendation
- Cost estimate (monthly)

## Layer 2: Chips & Hardware
- Recommended GPU tier (consumer, workstation, data center)
- Memory requirements for model size
- Whether specialized hardware (TPUs, custom ASICs) makes sense

## Layer 3: Infrastructure & Platform
- Orchestration: Kubernetes, Docker, serverless?
- Key services: vector DB, model registry, monitoring
- Scaling strategy (auto-scale triggers, max capacity)

## Layer 4: Models
- Build vs fine-tune vs use API
- Recommended base models for this use case
- Model serving strategy (latency vs cost tradeoff)

## Layer 5: Applications
- User-facing integration pattern
- Feedback loop design (how user data improves the model)
- Deployment pipeline (CI/CD for ML)

For each layer, flag:
- ⚡ Quick wins (can implement today)
- 🔧 Requires engineering effort
- 💰 Cost implications

Keep recommendations practical. Prefer managed services for teams < 5 engineers.
Prefer open-source for teams that need full control.
```

## When to Use
- Starting a new AI/ML project from scratch
- Migrating from prototype to production
- Evaluating build vs buy decisions across the stack
- Preparing for GTC 2026 announcements and new NVIDIA tooling

## Example Input
> "Building a RAG-based customer support agent for a SaaS product with 50K users. Team of 3 engineers. Budget: $2K/month for infra."

---

💡 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes the complete 5-Layer Production Blueprint with cost calculators, vendor comparison matrices, scaling playbooks for each layer, and GTC 2026-specific migration guides for Vera Rubin and Feynman architectures.
