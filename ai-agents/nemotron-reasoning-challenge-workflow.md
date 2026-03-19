# 🧠 Nemotron Reasoning Challenge Workflow

> Build and evaluate reasoning benchmarks for your AI agents using NVIDIA's Nemotron challenge framework (March 2026).

## The Prompt

```
You are a Reasoning Benchmark Engineer. I need to create a structured evaluation 
pipeline for testing LLM reasoning capabilities, inspired by NVIDIA's Nemotron 
Reasoning Challenge (GTC 2026).

## Context
- Model(s) under test: [MODEL_NAMES]
- Domain: [DOMAIN — e.g., code generation, math, logic, planning]
- Current baseline accuracy: [BASELINE or "unknown"]

## Tasks

1. **Benchmark Design**
   - Generate 10 multi-step reasoning problems in my domain
   - Each problem must require ≥3 logical steps
   - Include chain-of-thought reference solutions
   - Tag difficulty: easy / medium / hard / expert

2. **Evaluation Criteria**
   - Correctness (binary: right/wrong)
   - Reasoning trace quality (1-5 scale)
   - Step count efficiency (fewer = better)
   - Hallucination detection (any fabricated facts?)

3. **Quick Scoring Script**
   Output a Python script that:
   - Sends each problem to the model API
   - Parses the reasoning trace
   - Scores against reference solutions
   - Outputs a summary table with pass rate, avg quality, avg steps

Format output as a ready-to-run evaluation kit.
```

## When to Use

- Comparing models for reasoning-heavy tasks (code review, debugging, architecture)
- Building internal benchmarks before adopting a new LLM
- Preparing submissions for reasoning competitions

## Example Output

The prompt generates a complete evaluation kit: 10 graded problems, scoring rubric, and a Python script that automates the benchmark run.

## Limitations (Free Version)

- Single domain, 10 problems
- Basic scoring only

---

### 🔥 Want the full pipeline?

The **PRO version** includes:
- 50+ problems across 5 domains (code, math, logic, planning, multi-modal)
- Multi-model tournament runner (GPT-5.4 vs Claude Opus vs Nemotron vs open-source)
- Statistical significance testing (bootstrap CI)
- Cost-per-correct-answer calculator
- CI/CD integration (run benchmarks on every model update)

**[Get AI Dev Toolkit — $9 → 218 production-ready resources](https://ai-dev-toolkit-five.vercel.app)**
