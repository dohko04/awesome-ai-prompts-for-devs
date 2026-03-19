# Kilo Code Multi-Model Coding Workflow 🎯

> Set up Kilo Code as your free, multi-model AI coding agent. Route tasks to the best model (MiniMax M2.7, GPT-5.4, Claude Sonnet 4.6) based on complexity.

## The Prompt

```
You are an expert in Kilo Code, the free multi-model AI coding agent that lets developers choose between different LLMs for different tasks.

I'm setting up Kilo Code for my project:
- Language/framework: [e.g., TypeScript/Next.js, Python/FastAPI, Rust]
- Project size: [small/medium/large codebase]
- Budget: [free tier only / willing to pay for API keys]

Help me configure an optimal multi-model workflow:

1. **Model Selection Strategy**
   - Quick fixes & simple tasks → fastest/cheapest model
   - Complex refactors & architecture → deepest reasoning model
   - Code review & documentation → balanced model
   - Map each task type to the best available model

2. **Kilo Code Setup**
   - Install and configure the extension
   - Set up API keys for each provider
   - Configure model routing preferences
   - Set context window and token limits per model

3. **Workflow Configuration**
   - Create task-specific presets (bug fix, feature, refactor, review)
   - Set up project-level AGENTS.md for Kilo Code
   - Configure file inclusion/exclusion patterns
   - Set cost alerts and usage tracking

4. **Cost Optimization**
   - Use free models (MiniMax M2.7 free tier) for routine tasks
   - Reserve expensive models for complex reasoning
   - Track daily/weekly spend per model
   - Set hard budget caps

Output specific configs and the AGENTS.md template.
```

## Recommended Model Routing

| Task Type | Best Model | Why |
|-----------|-----------|-----|
| Quick fixes | MiniMax M2.7 | Free, fast, good context |
| Complex refactors | GPT-5.4 / Claude Opus 4.6 | Deep reasoning |
| Code review | Claude Sonnet 4.6 | 1M context, balanced |
| Documentation | MiniMax M2.7 | Cost-effective, good prose |
| Architecture decisions | GPT-5.4 | Strong at system design |

## AGENTS.md Template for Kilo Code

```markdown
# Project AI Configuration

## Models
- Default: minimax-m2.7
- Complex: gpt-5.4
- Review: claude-sonnet-4.6

## Rules
- Always run tests after code changes
- Never modify files outside /src without asking
- Use TypeScript strict mode
- Follow existing code patterns
```

## Limitations of This Free Version

This gives you a working single-project setup. The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:

- 🔀 **Intelligent auto-routing engine** (automatically picks model based on task complexity scoring)
- 📊 **Cost tracking dashboard** (real-time spend per model, per project, per week)
- 🧪 **A/B quality testing framework** (compare model outputs on same tasks)
- 🏢 **Team rollout playbook** (standardize multi-model workflows across 5-50 devs)
- 🔄 **Model migration scripts** (switch providers without changing prompts)

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — 124 free prompts for AI-powered development*
