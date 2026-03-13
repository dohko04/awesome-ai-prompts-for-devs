# Claude Sonnet 4.6 — 1M Context Codebase Workflow (FREE)

> Sonnet 4.6 is now the default free model on claude.ai, preferred over Opus 4.6 59% of the time in Claude Code, with a 1M context window in beta. This workflow helps you leverage that massive context for real codebase analysis.

## The Prompt

```
You are a senior software architect using Claude Sonnet 4.6 with a 1M token context window.

I'm going to paste my entire codebase (or large portions of it). Your job:

1. **Codebase Map** — Build a mental model of the architecture:
   - Entry points, dependency graph, data flow
   - Identify the 5 most critical files and why

2. **Cross-File Analysis** — Find issues that only appear when you see the full picture:
   - Circular dependencies
   - Inconsistent error handling patterns
   - Dead code paths
   - Type mismatches across module boundaries

3. **Refactoring Plan** — Prioritized list of improvements:
   - Risk level (safe/moderate/risky)
   - Estimated impact on maintainability
   - Dependencies between refactors

Output format: Start with a 1-paragraph executive summary, then detailed sections.
```

## When to Use This

- Onboarding to a new codebase
- Pre-refactoring analysis
- Architecture reviews
- Finding cross-file bugs that linters miss

## Tips

- Sonnet 4.6 at $3/$15 per MTok is 5x cheaper than Opus 4.6 for this kind of analysis
- For repos > 1M tokens, prioritize: src/ > tests/ > config/
- Combine with `find . -name "*.ts" | head -100 | xargs cat` to prepare input

---

> 🔥 **Want the full pipeline?** The PRO version includes: context budget optimizer (fit any repo into 1M tokens), multi-pass analysis (architecture → security → performance), automated chunking strategies, and cost comparison calculator across all frontier models.
>
> **[Get the AI Dev Toolkit — 127+ pro resources for $9](https://ai-dev-toolkit-five.vercel.app)**
