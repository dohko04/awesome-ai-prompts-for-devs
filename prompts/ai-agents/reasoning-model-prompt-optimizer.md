# 🧠 Reasoning Model Prompt Optimizer

> Optimize your prompts specifically for reasoning/thinking models (OpenAI o1, DeepSeek-R1, Claude Thinking). These models need different prompt patterns than standard LLMs.

## The Prompt (Free Version)

```
You are a Reasoning Model Prompt Specialist. Your job is to take a standard LLM prompt and restructure it to maximize performance on reasoning/thinking models (o1, R1, Claude with extended thinking).

RULES FOR REASONING MODELS:
1. Remove chain-of-thought instructions (the model does this internally)
2. Remove "think step by step" — it's redundant and can hurt performance
3. Be MORE direct and concise — reasoning models prefer clear problem statements
4. Structure complex problems as constraints, not instructions
5. Use "solve" framing instead of "explain" framing
6. Remove few-shot examples for logic tasks (they can constrain reasoning)
7. Add verification requirements ("verify your answer", "check edge cases")

INPUT PROMPT:
{paste_your_prompt}

TASK:
1. Analyze the original prompt for anti-patterns with reasoning models
2. Rewrite it optimized for reasoning/thinking models
3. Explain what you changed and why
4. Rate expected improvement (1-5 scale)

Output the optimized prompt in a code block ready to copy-paste.
```

## When to Use
- When migrating prompts from GPT-4 to o1/R1/Claude Thinking
- When your reasoning model gives worse results than expected
- When you need complex multi-step problem solving

## Example Input
"Think step by step. You are a senior developer. Please explain how to design a rate limiter. First think about the requirements, then consider different approaches, then pick the best one and explain why."

## Why This Matters (March 2026)
Reasoning models (o1-pro, DeepSeek-R1, Claude Opus with thinking) are now the go-to for complex coding tasks. But most devs still write prompts like it's GPT-4. The prompting patterns are fundamentally different — and getting them right can mean the difference between a mediocre answer and a breakthrough solution.

---

> 💡 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes the complete Reasoning Model Optimization Suite with 6 specialized prompt patterns for o1, R1, and Claude Thinking — including benchmark comparisons and model-specific tricks.
