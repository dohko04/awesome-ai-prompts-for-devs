# Multi-AI Tool Orchestration Strategy

> Most devs now juggle 2-4 AI tools daily. This prompt helps you design an optimal workflow that uses each tool for what it's best at — instead of fighting with one tool for everything.

## The Prompt

```
You are an AI Workflow Architect specializing in multi-tool developer setups. Help me design an orchestrated workflow across my AI tools.

## My Current Tools
List the AI tools I use (check all that apply):
- **Code generation:** [Claude Code / GitHub Copilot / Cursor / Codex / Windsurf / other]
- **Chat/reasoning:** [Claude / ChatGPT / Gemini / other]
- **Search/research:** [Perplexity / Phind / other]
- **Specialized:** [v0 for UI / Midjourney / other]

## My Development Context
- **Primary language(s):** [e.g., TypeScript, Python]
- **Project type:** [web app / API / CLI / data pipeline / mobile / other]
- **Solo or team:** [solo / team of N]
- **IDE:** [VS Code / JetBrains / Neovim / other]

## Design My Optimal Workflow

### 1. Tool-Task Mapping
For each phase of my development cycle, recommend which tool to use and WHY:

| Dev Phase | Primary Tool | Why This Tool Wins | Fallback Tool |
|-----------|-------------|-------------------|---------------|
| Planning/Architecture | | | |
| Scaffolding/Boilerplate | | | |
| Feature Implementation | | | |
| Debugging | | | |
| Code Review | | | |
| Testing | | | |
| Documentation | | | |
| Refactoring | | | |
| Research/Learning | | | |

### 2. Context Handoff Protocol
Design how I pass context between tools efficiently:
- What context files to maintain (e.g., AGENTS.md, .cursorrules, CLAUDE.md)
- How to structure project context so ANY tool can pick it up
- Template for "handoff notes" when switching tools mid-task
- Which tool should be the "source of truth" for project knowledge

### 3. Prompt Templates Per Tool
Give me a reusable prompt template optimized for each of my tools' strengths:
- Tool A: [optimized for its best capability]
- Tool B: [optimized for its best capability]
- Include model-specific tips (e.g., "Claude excels at long context", "Copilot is fastest for inline completions")

### 4. Anti-Patterns to Avoid
List the top 5 mistakes devs make when using multiple AI tools:
- Redundant context loading
- Tool-switching overhead
- Conflicting code styles
- [identify others based on my specific setup]

### 5. Weekly Workflow Template
Design a concrete weekly rhythm:
- Monday: [which tools for planning]
- During sprints: [which tools for implementation]
- Code review days: [which tools for review]
- Friday: [which tools for docs/cleanup]

### 6. Cost Optimization
Given my tool set, recommend:
- Which subscriptions are worth keeping
- Where free tiers are sufficient
- Estimated monthly cost for optimal setup
- ROI calculation: hours saved vs subscription costs

## Output Format
Practical, actionable workflow I can start using tomorrow. Include specific keybindings/shortcuts where relevant. No theory — just the playbook.
```

## When to Use This

- You're paying for 3+ AI tool subscriptions and aren't sure which to keep
- Your team has no standard for which AI tool to use when
- You're spending more time switching between tools than coding
- Starting at a new company and setting up your AI workflow from scratch

## Real-World Context

According to the 2026 Pragmatic Engineer survey, 95% of devs use AI weekly and most juggle 2-4 tools. The top combo: Claude Code for heavy coding + a chatbot for reasoning + Copilot for inline suggestions. But most devs haven't optimized how these tools work *together*.

## Pro Tips

- Run this prompt once, then refine after 2 weeks of actually using the workflow
- Share the output with your team to standardize tooling
- Re-run when a major new tool launches

---

> 🚀 **Want the complete Multi-Tool Playbook?** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) includes ready-to-use context files (.cursorrules, CLAUDE.md, .github/copilot), IDE-specific configs, and 30+ prompts optimized per tool. **$9 one-time.**
