# 📏 LLM Output Evaluator & Benchmark Designer

> Systematically evaluate and score LLM outputs for your specific use case. Build custom benchmarks, detect regressions, and choose the right model — with data, not vibes.

## The Prompt

```
You are an LLM Evaluation Engineer. Help me build a systematic evaluation framework for my AI-powered feature.

## My Use Case
- Application: [WHAT YOUR APP DOES]
- LLM task: [WHAT THE LLM DOES: e.g., "generates SQL from natural language", "summarizes support tickets", "extracts data from invoices"]
- Current model: [MODEL NAME]
- Considering: [ALTERNATIVE MODELS, if any]
- Volume: ~[NUMBER] calls/day
- Acceptable latency: [MAX MS]
- Budget: $[AMOUNT]/month

## Build My Evaluation Framework

### Step 1: Define Evaluation Dimensions
For my specific use case, define 4-6 scoring dimensions. Examples:
- **Correctness** — Does the output match the expected result?
- **Completeness** — Are all required elements present?
- **Format Compliance** — Does it follow the required schema/format?
- **Safety** — No hallucinations, no harmful content?
- **Latency** — Response time acceptable?
- **Cost Efficiency** — Cost per successful output?

For each dimension, provide:
- Clear definition
- Scoring rubric (1-5 scale with examples of each score)
- Weight (how important is this dimension, 0.0-1.0)

### Step 2: Generate Test Cases
Create 20 test cases covering:
- 5 **Happy path** — typical, well-formed inputs
- 5 **Edge cases** — unusual but valid inputs  
- 5 **Adversarial** — inputs designed to break the model
- 5 **Regression** — cases that previously failed

For each test case, provide:
```json
{
  "id": "TC-001",
  "category": "happy_path",
  "input": "...",
  "expected_output": "...",
  "evaluation_criteria": {
    "must_contain": [],
    "must_not_contain": [],
    "format_regex": "",
    "semantic_match_threshold": 0.85
  }
}
```

### Step 3: Scoring Script
Generate a Python evaluation script that:
- Runs all test cases against the LLM
- Scores each dimension automatically where possible
- Flags cases needing human review
- Produces a summary report with:
  - Overall score (weighted average)
  - Score breakdown by dimension
  - Score breakdown by test category
  - Pass/fail rate
  - Average latency & cost
  - Comparison table (if multiple models)

### Step 4: Regression Detection
Define alerts for:
- Overall score drops > 5% from baseline
- Any dimension drops below minimum threshold
- New failure on previously passing test case
- Latency P95 exceeds SLA

## Output Format
Provide the complete framework as:
1. Evaluation config (YAML)
2. Test cases (JSON)
3. Scoring script (Python)
4. CI integration snippet (GitHub Actions)
```

## When to Use

- Before switching LLM providers (compare models objectively)
- After prompt changes (detect regressions)
- Monthly quality audits
- When scaling up and need to justify model costs

## Pro Tips

- Start with 20 test cases, grow to 100+ over time
- Save every production failure as a new regression test case
- Run evals on every prompt change in CI/CD
- Use a cheaper model (GPT-4o-mini) as an "LLM judge" for semantic scoring

---

> 💡 **Want production-ready eval pipelines?** The [Complete AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes **ready-to-run eval scripts**, pre-built scoring rubrics for 10+ common LLM tasks, model comparison dashboards, and cost optimization calculators.
