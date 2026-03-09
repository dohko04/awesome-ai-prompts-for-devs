# AI Coding Agent Router — Pick the Right Tool for Each Task

> 🔥 **Trending (March 2026):** With 7+ AI coding agents available (Cursor, Claude Code, Codex, Kiro, Windsurf, Copilot, Cody), the hardest problem isn't using them — it's knowing *which one to use when*. This prompt builds your personal decision framework.

## The Prompt

```markdown
You are a senior developer who has extensively used all major AI coding agents in 2026. Help me build a personalized routing strategy for my workflow.

## My Setup
- Primary language(s): {{LANGUAGES}}
- Project type: {{PROJECT_TYPE}} (e.g., web app, API, mobile, CLI, infra)
- Team size: {{TEAM_SIZE}}
- Current tools: {{CURRENT_TOOLS}} (e.g., "Cursor Pro + Claude Code Max")
- Monthly budget for AI tools: ${{BUDGET}}
- Pain points: {{PAIN_POINTS}} (e.g., "large refactors break things", "slow PR reviews")

## Task
Create a practical routing guide that tells me which AI agent to use for each type of task. Be specific and opinionated — I don't want "it depends."

### 1. Task-to-Tool Router
Build a decision matrix for these common dev tasks:
- Writing new features (greenfield code)
- Refactoring existing code (>500 lines changed)
- Debugging production issues
- Writing/fixing tests
- Code review and PR feedback
- DevOps (Dockerfiles, CI/CD, IaC)
- Documentation and READMEs
- Database migrations and queries
- Multi-file architectural changes
- Quick one-liners and snippets

For each task, specify:
- **Best tool** and why
- **Runner-up** as fallback
- **Avoid** (which tool is worst for this)
- **Key config** (model, mode, context settings)

### 2. Context Strategy per Tool
- Cursor: What goes in .cursor/rules vs project-level instructions?
- Claude Code: How to structure CLAUDE.md + AGENTS.md for agent teams?
- Codex: When to use vs Claude Code for async tasks?
- MCP: Which servers to connect to which client?

### 3. Workflow Combos
Design 2-3 multi-tool workflows:
- **Explore → Implement → Review**: e.g., Claude Code for understanding codebase → Cursor for writing → Copilot for review
- **Parallel agents**: When to spin up Claude Code agent teams vs Cursor background agents
- **The escape hatch**: When to drop AI and code manually (be honest!)

### 4. Cost Optimization
Given my ${{BUDGET}}/month budget:
- Optimal subscription combo
- When to use each tool to maximize value
- Token-saving strategies (context pruning, smart model selection)
- Which free tiers are actually worth using

## Output Format
- Markdown table for the task router
- Mermaid flowchart for decision logic
- Concrete config files I can copy-paste
- Monthly cost breakdown

## Rules
- Be brutally honest about each tool's weaknesses
- Include specific version/model recommendations (not just "use Claude")
- Account for March 2026 features (Agent Teams, Kiro specs, Codex async)
```

## When to Use

- You're paying for 2+ AI coding tools and not sure you're using them optimally
- Your team is standardizing on AI tools and needs a shared strategy
- You want to stop context-switching between tools randomly
- You're evaluating whether to add/drop a tool from your stack

## Pro Tips

1. **Don't use one tool for everything** — Claude Code crushes multi-file refactors but Cursor is faster for in-editor flow
2. **Match the model to the task** — use fast models (Sonnet) for autocomplete, thinking models (Opus) for architecture
3. **Set up MCP servers once, use everywhere** — same MCP servers work in Claude Code, Cursor, and Xcode 26.3
4. **Track your actual usage** — most devs overestimate how much they use their secondary tool

---

> 💡 **Want pre-built configs for every tool?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes optimized .cursorrules, CLAUDE.md templates, MCP configs, and multi-tool workflow guides for 10+ project types — plus 100+ engineering prompts for $9.
