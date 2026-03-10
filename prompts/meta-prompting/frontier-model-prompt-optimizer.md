# 🚀 Frontier Model Prompt Optimizer (GPT-5.4 / Gemini 3.1 Pro)

> **Trending (March 2026):** GPT-5.4 just launched with 1M token context and mid-response planning. Gemini 3.1 Pro scores 77.1% on ARC-AGI-2. Your old prompts are leaving performance on the table — this optimizer rewrites them for the new frontier.

## The Prompt (Free Version)

```
You are a Prompt Migration Specialist. I'm upgrading from [CURRENT_MODEL] to [TARGET_MODEL].

Target model capabilities (March 2026):
- GPT-5.4: 1M token context, mid-response planning ("steering"), enhanced coding/reasoning
- Gemini 3.1 Pro: 1M token context, 77.1% ARC-AGI-2, multimodal (text/image/audio/video/code)
- Claude Sonnet 4.6: Near-Opus quality at Sonnet pricing, strong agentic coding

Take my existing prompt below and optimize it for the target model by:

1. **Context Window Exploitation**
   - If the task involves large codebases/docs, restructure to leverage 1M tokens
   - Add instructions to process ALL context before responding (no lazy summarization)
   - Include "read everything first, then synthesize" directives

2. **Reasoning Chain Optimization**
   - For GPT-5.4: Use its "steering" capability — instruct it to plan steps mid-response
   - For Gemini: Leverage multimodal — reference images/diagrams if applicable
   - For Claude: Use XML tags for structured sections, leverage agentic tool use

3. **Output Quality Upgrades**
   - Add self-verification step: "Before responding, verify your answer against [criteria]"
   - Request confidence scores for each recommendation
   - Add "if unsure, say so" guardrail

4. **Anti-Pattern Removal**
   - Remove unnecessary "you are an expert" fluff (frontier models don't need it)
   - Replace vague instructions with specific, measurable criteria
   - Remove token-saving hacks that are no longer needed with 1M context

Output format:
---
## Original Prompt Analysis
- Model assumptions detected: [what model era this was written for]
- Performance limiters found: [what's holding it back]

## Optimized Prompt
```
[the rewritten prompt]
```

## What Changed & Why
| Change | Reason | Expected Impact |
|--------|--------|----------------|
| ... | ... | ... |

## Model-Specific Tips
[2-3 tips for getting the most out of the target model]
---

My existing prompt to optimize:
"""
[PASTE YOUR PROMPT HERE]
"""

Target model: [GPT-5.4 / Gemini 3.1 Pro / Claude Sonnet 4.6]
```

---

## 🚀 Want the Full Version?

The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:
- ✅ Full migration pipeline: batch-optimize ALL your prompts at once
- ✅ Model-specific prompt templates for GPT-5.4, Gemini 3.1, Claude 4.6
- ✅ A/B testing framework: measure prompt performance across models
- ✅ Cost analyzer: compare $/quality across frontier models
- ✅ 70+ production-ready prompts already optimized for 2026 models

[**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
