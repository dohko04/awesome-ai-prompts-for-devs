# Context Budget Planner — Fit More Signal Into Your AI's Context Window

> 🔥 **Trending (March 2026):** Context engineering is the new prompt engineering. With models supporting 200K+ tokens, the bottleneck isn't size — it's signal-to-noise ratio. Engineers who master context budgeting get dramatically better outputs.

## The Prompt

```markdown
You are a context engineering specialist. Help me plan exactly what context to feed my AI coding agent for maximum output quality while minimizing token waste.

## My Situation
- **Model:** [e.g., Claude Sonnet 4.6, GPT-5, Gemini 2.5 Pro]
- **Context window:** [e.g., 200K tokens]
- **Task:** [describe what you want the AI to do]
- **Codebase size:** [e.g., 50 files, 15K lines]

## Create a Context Budget:

### 1. Token Budget Allocation
Break my context window into zones:
| Zone | % Budget | Purpose |
|------|----------|---------|
| System/Instructions | ~5% | Role, conventions, constraints |
| Architecture Context | ~15% | Types, interfaces, key abstractions |
| Direct Task Files | ~40% | Files being created/modified |
| Reference Examples | ~20% | Similar existing code for pattern matching |
| Test Context | ~10% | Existing test patterns to follow |
| Buffer | ~10% | For AI reasoning and output |

### 2. File Priority Ranking
Given my task, rank which files to include:
- **Must include** (blocks progress without them)
- **Should include** (improves quality significantly)
- **Nice to have** (marginal improvement)
- **Exclude** (noise, wastes tokens)

### 3. Context Compression Techniques
For each file category, show me how to:
- Extract only relevant types/interfaces (skip implementations)
- Summarize long files into "context headers"
- Use code snippets instead of full files
- Create `.context/` directory with pre-compressed project summaries

### 4. Dynamic Context Loading
Design a system where context changes based on task:
- Feature work → load feature module + shared types
- Bug fix → load error logs + failing test + related module
- Refactoring → load full module + dependent modules + tests

### 5. Context Freshness Rules
- When to refresh context (stale files after N changes)
- How to detect context drift (AI referencing old patterns)
- Session restart triggers
```

## Why This Works

A 200K context window full of irrelevant code performs worse than a 10K window with exactly the right files. Context engineering is about curation, not capacity. This prompt helps you build a systematic approach instead of dumping your entire codebase and hoping for the best.

> 💡 **Want the full version?** The complete prompt includes a context budget calculator script, pre-built `.context/` directory templates for 6 project types, and a dynamic context loader that auto-selects files based on your git diff.
>
> 👉 **[Get the AI Dev Toolkit — 55+ pro prompts for $9](https://ai-dev-toolkit-five.vercel.app)** — Pay with ETH, instant access.

---
*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) · Built by [Dohko](https://github.com/dohko04)*
