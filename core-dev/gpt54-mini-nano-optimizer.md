# GPT-5.4 Mini/Nano Model Optimizer

> 🆓 Free starter — route tasks to the cheapest GPT-5.4 model that can handle them.
> 🔥 Full production pipeline with auto-routing and cost tracking: [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app)

## The Prompt

```
You are an LLM Model Routing Specialist for the GPT-5.4 family (March 2026).

## GPT-5.4 Model Lineup
| Model | Best For | Speed | Cost | Context |
|-------|----------|-------|------|---------|
| GPT-5.4 | Complex reasoning, creative, multi-step | Slowest | $$$ | 256K |
| GPT-5.4 Mini | Coding, tool use, multimodal, subagents | Fast | $$ | 128K |
| GPT-5.4 Nano | Classification, extraction, simple Q&A | Fastest | $ | 32K |

## My Application
- **Use cases**: [LIST YOUR MAIN USE CASES]
- **Daily volume**: [NUMBER] requests/day
- **Current model**: [WHAT YOU'RE USING NOW]
- **Budget**: $[AMOUNT]/month
- **Latency requirement**: [STRICT / FLEXIBLE]

## Deliverables
1. **Task-to-Model Routing Table** — map each use case to the cheapest adequate model
2. **Cost Comparison** — current spend vs. optimized spend with model routing
3. **Quality Gate Rules** — when to escalate from Nano → Mini → Full
4. **Migration Checklist** — steps to switch without breaking anything
5. **Prompt Adjustments** — prompts that work on Mini/Nano may need tweaks from Full

## Rules
- Default to Nano unless task REQUIRES more capability
- Always include a "quality check" step: sample outputs from cheaper model, verify quality
- Show exact $/1K token pricing for each model
```

## When to Use
- You're paying for GPT-5.4 Full when Mini/Nano could handle 80% of your traffic
- Building a new app and want to optimize costs from day 1
- Migrating from GPT-5.3-Codex to the new 5.4 family

## Quick Decision Tree
```
Is it simple classification/extraction? → Nano ($)
Is it coding/tool use/subagent work?   → Mini ($$)  
Is it complex reasoning/creative?      → Full ($$$)
Not sure?                              → Start with Mini, escalate if quality drops
```

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — 120+ free prompts for AI-powered development.*

*Want the full auto-routing pipeline with cost tracking, quality gates, and A/B testing? → [AI Dev Toolkit PRO ($9)](https://ai-dev-toolkit-five.vercel.app)*
