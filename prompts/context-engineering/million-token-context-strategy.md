# 📚 Million-Token Context Strategy Planner

> Plan how to effectively use 1M+ token context windows (GPT-5.2, Gemini 2.5) without drowning the model in noise.

## The Prompt (Free Version)

```
You are a Context Window Strategist for large language models with 1M+ token context windows.

MY SITUATION:
- Model: {model_name} with {context_size} token window
- Task: {what_you_need_the_llm_to_do}
- Available data: {describe_your_codebase/docs/data}
- Total data size estimate: {approximate_tokens}

PROBLEM: Having a huge context window doesn't mean "dump everything in." Models still have attention degradation, cost implications, and the "lost in the middle" problem.

TASK — Design my context loading strategy:

1. CONTEXT TRIAGE: Classify my data into:
   - 🔴 MUST INCLUDE (directly relevant, put near prompt)
   - 🟡 HELPFUL (include if budget allows, position carefully)
   - 🟢 SKIP (available but not worth the tokens/cost)

2. POSITIONING STRATEGY:
   - What goes at the START (high attention)
   - What goes in the MIDDLE (lower attention zone)
   - What goes at the END (near the prompt, high attention)
   - Use the "bookend" pattern for critical info

3. CHUNKING PLAN:
   - How to split large documents
   - When to summarize vs include raw
   - Compression techniques (structured summaries, key-value extraction)

4. COST/QUALITY TRADEOFF:
   - Estimate tokens used vs quality gained
   - Recommend whether full context or RAG is better for this task

Output a concrete loading plan I can implement.
```

## When to Use
- When working with GPT-5.2 (1M tokens) or Gemini 2.5 Pro
- When doing whole-codebase analysis or migration
- When you need to process entire documentation sets

## Why This Matters (March 2026)
GPT-5.2's 1M token context and Gemini's 2M tokens are game-changers — but most devs waste them by either under-utilizing (old habits from 8K days) or over-stuffing (dumping everything). Strategic context loading is the new skill that separates good AI-assisted devs from great ones.

---

> 💡 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes the complete Context Engineering Suite: 7 prompts covering context budgeting, dynamic routing, codebase indexing strategies, and ready-to-use context loading templates for different project sizes.
