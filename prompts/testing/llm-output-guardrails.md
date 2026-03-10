# 🛡️ LLM Output Guardrails & Eval Prompt

> Design validation layers that catch hallucinations, enforce output schemas, and grade LLM responses before they reach users.

## The Prompt

```
You are an LLM Output Quality Engineer. Help me design guardrails and evaluation layers for my AI-powered application.

## Context
- Application type: [chatbot / code generator / data extractor / content writer]
- LLM provider: [OpenAI / Anthropic / local model / multi-provider]
- Output format: [free text / JSON / code / structured data]
- Risk level: [low - internal tool / medium - user-facing / high - financial/medical/legal]

## Tasks

### 1. Output Validation Layer
Design validation checks for my LLM outputs:
- **Schema validation**: Ensure outputs match expected structure
- **Content safety**: Flag toxic, biased, or harmful content
- **Hallucination detection**: Cross-reference claims against provided context
- **PII detection**: Catch leaked personal data in responses
- **Format compliance**: Verify output follows required format

### 2. Eval Suite Design
Create an evaluation framework:
- Define 5-10 test cases covering edge cases for my use case
- Include golden answers for regression testing
- Design a scoring rubric (1-5 scale) for: accuracy, relevance, safety, format
- Suggest automated metrics (BLEU, ROUGE, semantic similarity where applicable)

### 3. Guardrail Rules
Write guardrail rules as pseudocode:
- Input sanitization (prompt injection defense)
- Output filtering (banned topics, format enforcement)
- Confidence thresholds (when to escalate to human)
- Rate limiting and abuse detection patterns

### 4. Monitoring Dashboard Spec
Define what to track in production:
- Latency percentiles (p50, p95, p99)
- Token usage and cost per request
- Guardrail trigger rates
- User feedback correlation

Provide concrete, copy-paste-ready implementations where possible.
```

## When to Use
- Before deploying any LLM-powered feature to production
- When you need to validate AI outputs systematically
- Setting up CI/CD pipelines with LLM eval steps
- After incidents caused by bad LLM outputs

## Example Output Structure
The prompt generates:
1. Validation middleware code skeleton
2. Test case templates
3. Scoring rubric table
4. Monitoring checklist

## Tips
- Start with the highest-risk outputs first
- Use LLM-as-judge for subjective quality (but validate the judge too)
- Keep golden test sets small but representative (20-50 cases)
- Track guardrail trigger rates — too high means your prompt needs work

---

> 🔥 **Want production-ready guardrail code (Python + TypeScript), pre-built eval pipelines, CI/CD integration configs, and advanced hallucination detection?** Check out [AI Dev Toolkit PRO](https://dohko04.gumroad.com/l/ai-dev-toolkit)

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs)*
