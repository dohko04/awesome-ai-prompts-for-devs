# 🏛️ The System Design Architect

> **When to use:** You need to design a new system or feature from scratch with clear architecture decisions.

## Prompt Template

```
Design a system for: [describe the feature/product]

Requirements:
- Users: [expected scale — 100? 10K? 1M?]
- Tech stack: [your current stack or "recommend one"]
- Constraints: [budget, timeline, team size, existing systems]
- Key features: [list 3-5 core features]

Provide:
1. High-level architecture diagram (ASCII art)
2. Component breakdown with responsibilities
3. Data flow for the main use case
4. Database schema (key tables only)
5. Top 3 technical risks and mitigations
6. Build vs Buy decisions
7. Phased implementation plan (MVP → V2 → Scale)
```

## Example Output

> ```
> ┌──────────┐     ┌──────────┐     ┌──────────┐
> │  Client  │────▶│ API GW   │────▶│ Auth Svc │
> │  (React) │     │ (Kong)   │     │ (JWT)    │
> └──────────┘     └────┬─────┘     └──────────┘
>                       │
>                  ┌────▼─────┐     ┌──────────┐
>                  │ Order Svc│────▶│ Postgres │
>                  └────┬─────┘     └──────────┘
>                       │
>                  ┌────▼─────┐
>                  │ Queue    │
>                  │ (SQS)   │
>                  └──────────┘
> ```
>
> **Phase 1 (MVP, 2 weeks):** Monolith with Auth + Orders. Single Postgres DB. Deploy on Railway/Render.
>
> **Risk #1:** Single DB becomes bottleneck at ~50K users → Mitigation: Read replicas + caching layer in Phase 2.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
