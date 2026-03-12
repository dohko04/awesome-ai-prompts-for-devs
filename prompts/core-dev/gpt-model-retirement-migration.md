# GPT Model Retirement Migration Guide

> Handle OpenAI model deprecations without breaking your app. Updated for GPT-5.1 → 5.3/5.4 migration (March 2026).

**Why now:** OpenAI retired GPT-5.1 on March 11, 2026, auto-migrating to GPT-5.3/5.4. Many devs hit unexpected behavior changes. This prompt helps you audit and migrate safely.

## The Prompt

```
You are an AI migration engineer. I'm migrating from [OLD_MODEL] to [NEW_MODEL] in my application.

MIGRATION AUDIT:
1. Analyze my current API calls and identify breaking changes:
   - Response format differences
   - Token counting changes
   - Pricing impact (calculate cost delta)
   - Behavior/quality regressions for my use case
   
2. Generate a migration checklist:
   - [ ] Update model parameter in all API calls
   - [ ] Adjust max_tokens if context window changed
   - [ ] Update temperature/top_p if defaults changed
   - [ ] Review system prompts for model-specific instructions
   - [ ] Update token counting logic (tiktoken encoding changes)
   - [ ] Run regression tests on critical outputs
   - [ ] Update cost monitoring/alerts
   - [ ] Add model fallback logic

3. Generate code for graceful model fallback:
   - Try primary model
   - Fall back to secondary on failure/deprecation
   - Log which model served each request
   - Alert on fallback activation

IMPORTANT:
- Flag any system prompt changes needed (newer models may interpret differently)
- Calculate estimated monthly cost change
- Identify prompts that might need retuning
```

## Quick Fallback Pattern

```python
import openai

MODELS = ["gpt-5.4", "gpt-5.3", "gpt-5.2"]  # priority order

async def resilient_completion(messages, **kwargs):
    for model in MODELS:
        try:
            return await openai.chat.completions.create(
                model=model, messages=messages, **kwargs
            )
        except openai.NotFoundError:
            continue  # model deprecated, try next
    raise RuntimeError("All models unavailable")
```

## When to Use

- OpenAI announces model retirement (happens every 2-3 months)
- Switching between model tiers to optimize cost
- Adding multi-model resilience to production apps

---

> 💡 **Want the full pipeline?** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) includes a complete Model Migration Pipeline with automated regression testing, cost calculators, prompt retuning workflows, and multi-provider fallback systems. $9 one-time.
