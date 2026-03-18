# Mistral Small 4 Unified Workflow 🎯

> One model for coding, reasoning, multimodal, and agentic tasks — use the 119B MoE Mistral Small 4 to replace your multi-model setup.

## The Problem

You're juggling multiple models for different tasks:
- GPT for reasoning, Claude for coding, a vision model for images
- Each has different APIs, rate limits, pricing, and prompt styles
- Context switching between models kills your workflow
- Costs multiply with every additional provider

## Quick Start: Unified Model Workflow

Paste this into your AI coding assistant when setting up Mistral Small 4:

```
You are an AI infrastructure architect. I want to consolidate my multi-model setup
into a single Mistral Small 4 deployment (119B MoE, 128 experts).

CURRENT SETUP:
- Coding: [Claude / GPT / Devstral / Codestral]
- Reasoning: [o3 / Magistral / DeepSeek R1]
- Multimodal: [GPT-4V / Pixtral / Gemini]
- Agentic: [separate agent model or same as above]
- Monthly spend: [$X across providers]

HELP ME:
1. **Migration Checklist** — What can Mistral Small 4 replace today vs what needs to stay
   - Map each use case to Small 4 capability (instruct/reasoning/vision/coding)
   - Flag any gaps where Small 4 underperforms (be honest)
   - Estimate cost savings from consolidation

2. **Prompt Adaptation Guide**
   - How to adapt my existing prompts for Small 4's format
   - Optimal system prompts for each mode (coding, reasoning, vision)
   - When to use extended thinking vs direct response
   - Temperature/top_p recommendations per task type

3. **API Integration Config**
   - Python client setup (mistralai SDK)
   - Fallback chain: Small 4 → backup model for edge cases
   - Rate limiting and retry logic
   - Cost tracking per-request

Output as working Python code + markdown guide. Include real API calls.
```

## Example: Quick API Setup

```python
# mistral_small4_client.py
from mistralai import Mistral
import os

client = Mistral(api_key=os.environ["MISTRAL_API_KEY"])

# Coding task
def code_with_small4(prompt: str, language: str = "python") -> str:
    response = client.chat.complete(
        model="mistral-small-4-2503",
        messages=[
            {"role": "system", "content": f"Expert {language} developer. Write clean, tested code."},
            {"role": "user", "content": prompt}
        ],
        temperature=0.1  # Low for code
    )
    return response.choices[0].message.content

# Reasoning task  
def reason_with_small4(prompt: str) -> str:
    response = client.chat.complete(
        model="mistral-small-4-2503",
        messages=[
            {"role": "system", "content": "Think step by step. Show your reasoning."},
            {"role": "user", "content": prompt}
        ],
        temperature=0.3  # Medium for reasoning
    )
    return response.choices[0].message.content

# Vision task
def analyze_image(image_url: str, question: str) -> str:
    response = client.chat.complete(
        model="mistral-small-4-2503",
        messages=[{
            "role": "user",
            "content": [
                {"type": "image_url", "image_url": {"url": image_url}},
                {"type": "text", "text": question}
            ]
        }]
    )
    return response.choices[0].message.content
```

## Key Specs

| Feature | Mistral Small 4 |
|---------|-----------------|
| Parameters | 119B (MoE, 128 experts) |
| Active params | ~24B per token |
| Context | 128K tokens |
| Modalities | Text + Vision |
| Modes | Instruct, Reasoning, Coding, Agentic |
| License | Apache 2.0 (open weights) |
| Self-host | Yes (vLLM, TGI, Ollama) |

## When to Use This

- Consolidating from 3+ model providers to one
- Starting a new project and want one model for everything
- Running on a budget and need to reduce API costs
- Self-hosting and want one model to serve all use cases

## Limitations (Free Version)

This gives you a basic unified workflow. The **PRO version** includes:
- 5-part production pipeline (model evaluator, prompt migration engine, cost optimizer, self-hosting configs, A/B testing framework)
- Head-to-head benchmarks vs GPT-5.4, Claude Opus 4.6, Gemini 2.5
- vLLM + Ollama self-hosting configs with GPU memory calculator
- Multi-model fallback router with automatic quality scoring

👉 **Get the full Mistral Small 4 Production Pipeline PRO:** [ai-dev-toolkit](https://ai-dev-toolkit-five.vercel.app)

---

*Based on Mistral Small 4 release (March 16, 2026) — 119B MoE unifying Devstral, Magistral, Pixtral into one model.*
