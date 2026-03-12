# 🔄 GPT-5.1 Deprecation Migration Checker

> **Context:** As of March 11, 2026, OpenAI retired all GPT-5.1 models (Instant, Thinking, Pro). Existing API calls will fail or auto-fallback. This prompt audits your codebase and gives you a migration plan.

## The Prompt

```markdown
You are an OpenAI API Migration Specialist. I need to migrate my codebase from GPT-5.1 to the current models after the March 11, 2026 deprecation.

## Model Mapping (Official)
- GPT-5.1 Instant → GPT-5.3 Instant (faster, cheaper)
- GPT-5.1 Thinking → GPT-5.4 Thinking (better reasoning)
- GPT-5.1 Pro → GPT-5.4 Pro (highest capability)

## Your Task

Analyze the code I provide and:

1. **Find all GPT-5.1 references** — model strings, environment variables, config files, hardcoded values
2. **Map each to the correct replacement** using the official mapping above
3. **Flag breaking changes:**
   - Response format differences between 5.1 and 5.3/5.4
   - Token limit changes (5.1 had 256K context, 5.4 has 1M)
   - Pricing differences (estimate cost impact)
   - Deprecated parameters that no longer work
4. **Generate a migration checklist** with:
   - Files to change (exact line numbers)
   - Environment variables to update
   - Test cases to verify behavior parity
   - Rollback plan if issues arise

## Output Format

### 🔍 Audit Summary
- Total GPT-5.1 references found: X
- Files affected: [list]
- Estimated effort: [hours]

### 📋 Migration Steps
[numbered, actionable steps]

### ⚠️ Breaking Changes
[any behavior differences to watch for]

### 💰 Cost Impact
[estimated cost change per 1M tokens]

### ✅ Verification Tests
[test cases to confirm successful migration]
```

## Usage

1. Paste this prompt into Claude, GPT-5.4, or your preferred LLM
2. Follow up by pasting your code files, configs, or `grep -r "gpt-5.1" .` output
3. Apply the generated migration plan

## Example Input

```
Here's my OpenAI config:
MODEL=gpt-5.1-thinking
FALLBACK_MODEL=gpt-5.1-instant

And my API call:
response = client.chat.completions.create(
    model="gpt-5.1-thinking",
    messages=messages,
    reasoning_effort="high"
)
```

## What This Covers

- ✅ Model string replacement mapping
- ✅ Breaking change detection
- ✅ Cost impact estimation
- ✅ Basic test cases

## What the Pro Version Adds

- 🔥 **Automated migration script** — finds and replaces across entire repos
- 🔥 **Multi-provider fallback chain** — GPT-5.4 → Claude Opus 4.6 → Gemini 3.1
- 🔥 **Cost optimization matrix** — when to use 5.3 vs 5.4 based on task complexity
- 🔥 **A/B testing framework** — run old vs new models in parallel, compare outputs
- 🔥 **Rollback automation** — feature flags for instant model switching
- 🔥 **CI/CD integration** — GitHub Actions workflow for model migration testing

> 🚀 **Get the full GPT-5.x Migration Pipeline Pro** → [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)

---

*Created by [Dohko](https://github.com/dohko04) · March 12, 2026*
