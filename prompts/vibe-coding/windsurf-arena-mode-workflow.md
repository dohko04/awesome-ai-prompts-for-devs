# Windsurf Arena Mode — Model Comparison Workflow

> **Category:** Vibe Coding · **Difficulty:** Intermediate · **Updated:** March 2026

Windsurf Wave 13 introduced Arena Mode — blind side-by-side model comparison with voting. This workflow helps you run structured model evaluations to find the best AI for YOUR codebase.

## The Prompt

```
You are an AI Model Arena Evaluator. I'm using Windsurf's Arena Mode to compare
models side-by-side on real coding tasks from my project.

Help me design a structured evaluation:

1. **Task Categories** — generate 5 representative coding tasks from my codebase:
   - Bug fix (medium complexity)
   - New feature (greenfield)
   - Refactor (existing code improvement)
   - Test generation (unit + integration)
   - Documentation (API docs from code)

2. **Evaluation Criteria** — for each Arena round, I'll rate:
   - Correctness (does it compile/run?)
   - Completeness (did it handle edge cases?)
   - Code quality (idiomatic, clean, maintainable?)
   - Context understanding (did it grok my codebase?)

3. **Decision Matrix** — after 5 rounds, generate a summary:
   - Which model won per category
   - Overall winner with confidence score
   - Cost-per-quality recommendation

My project uses: [TECH_STACK]
My current default model is: [CURRENT_MODEL]
Models I want to compare: [MODEL_A] vs [MODEL_B]
```

## How to Use

1. Open Windsurf → Enable Arena Mode in settings
2. Paste this prompt and fill in your stack details
3. Run each task category as a separate Arena round
4. Vote blindly, then reveal — track results
5. After 5 rounds, ask for the Decision Matrix summary

## Example Output

```
ARENA RESULTS — React + TypeScript Project
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Round 1 (Bug Fix):     Model A ✓  [Correct, handled null edge case]
Round 2 (Feature):     Model B ✓  [Better component structure]
Round 3 (Refactor):    Model A ✓  [Cleaner extraction pattern]
Round 4 (Tests):       TIE        [Both generated valid tests]
Round 5 (Docs):        Model B ✓  [More thorough API descriptions]

WINNER: Model B (3-2-0) — Confidence: 60%
RECOMMENDATION: Use Model B for feature work, Model A for debugging
```

## Why This Matters

Most devs pick a model once and never evaluate again. Arena Mode makes blind comparison trivial — but without a structured methodology, you're just vibing. This workflow gives you data-driven model selection.

---

> 🔒 **Want the full Arena Pipeline?** The PRO version includes automated scoring spreadsheets, 15-task evaluation suite, multi-IDE comparison (Cursor vs Windsurf vs Claude Code), and cost-per-quality calculator → [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)
