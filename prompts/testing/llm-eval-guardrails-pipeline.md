# 🛡️ LLM Eval & Guardrails Pipeline

Your AI features are only as good as your evals. This prompt designs a complete evaluation and guardrails pipeline so you can ship LLM-powered features with confidence — and catch regressions before users do.

## The Prompt

```
You are an LLM Ops engineer who specializes in evaluation and safety. I need to build an eval and guardrails pipeline for my LLM-powered feature.

My feature:
- **What it does:** {FEATURE_DESCRIPTION}
- **LLM provider:** {PROVIDER: OpenAI | Anthropic | Google | local}
- **Input type:** {INPUT: user text | structured data | code | documents}
- **Output type:** {OUTPUT: text response | JSON | code | classification}
- **Risk level:** {RISK: low (internal tool) | medium (user-facing) | high (financial/medical/legal)}

Build my eval + guardrails pipeline:

### 1. Eval Dataset Design
- Define 5 eval categories for my feature: happy path, edge cases, adversarial, regression, performance
- For each category, generate 5-10 test cases with:
  - Input
  - Expected output (or output criteria)
  - Why this test matters
- Show me how to store these as version-controlled fixtures (JSON/YAML)

### 2. Automated Eval Metrics
Design metrics for my specific output type:
- **If text:** Relevance score, factual accuracy, tone consistency, length compliance
- **If JSON:** Schema compliance, field accuracy, completeness
- **If code:** Syntax validity, test pass rate, security scan
- **If classification:** Precision, recall, F1, confusion matrix

For each metric, give me:
- How to compute it (LLM-as-judge, heuristic, or deterministic)
- Threshold for pass/fail
- Code to run it automatically

### 3. Input Guardrails
Build a pre-processing pipeline:
- Prompt injection detection (pattern matching + classifier)
- PII detection and redaction
- Input length and format validation
- Topic/intent classification (reject off-topic)
- Show implementation code for each guardrail

### 4. Output Guardrails
Build a post-processing pipeline:
- Hallucination detection (if RAG: verify against source docs)
- Toxicity/bias screening
- Output format validation (JSON schema, length limits)
- Confidence scoring — when to fallback to human review
- Sensitive data leak prevention in responses

### 5. CI/CD Integration
- GitHub Actions workflow that runs evals on every PR
- Eval score tracking over time (show me the dashboard schema)
- Automated alerts when eval scores drop below threshold
- A/B testing setup for prompt changes

### 6. Monitoring in Production
- What to log for every LLM call (structured schema)
- Key metrics to dashboard: latency, cost, success rate, guardrail trigger rate
- Anomaly detection: how to catch when the model starts behaving differently
- User feedback loop: thumbs up/down → eval dataset expansion

Output as:
- Implementation code (Python or TypeScript, specify {LANGUAGE})
- CI/CD config files
- A prioritized rollout plan (what to implement first)
```

## Example Usage

```
Feature: AI-powered code review bot that comments on PRs
Provider: Anthropic Claude Sonnet
Input: code diffs (unified diff format)
Output: structured JSON with review comments, severity, suggestions
Risk: medium (developer-facing, could give bad advice)
Language: TypeScript
```

## Tips

- Start with 20 hand-curated eval cases. Quality beats quantity early on.
- LLM-as-judge works surprisingly well — use a stronger model to eval a weaker one.
- Run evals on EVERY prompt change, not just code changes.
- Track eval scores over time — model updates from providers can silently regress your feature.

---

> 🚀 **Get production-ready eval templates.** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes complete eval pipelines, guardrail implementations, CI/CD configs, and monitoring dashboards — plug them into your project and ship with confidence.
