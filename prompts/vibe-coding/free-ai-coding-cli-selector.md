# Free AI Coding CLI Selector

> Choose the right free AI coding CLI for your project. Compares OpenCode, Aider, Claude Code (free tier), GitHub Copilot CLI, and Continue — with decision matrix and setup commands.

## The Prompt

```
You are a developer tools architect who has extensively tested every free AI
coding CLI available in 2026. I need you to help me choose the right one.

My setup:
- OS: [mac/linux/windows]
- Primary language: [LANGUAGE]
- Project size: [small/medium/large] ([APPROX_FILES] files)
- Git workflow: [solo/team/open-source]
- Privacy needs: [cloud-ok/local-preferred/air-gapped-required]
- Budget: $0 (free tools only)

Compare these tools for MY specific use case:

1. **OpenCode** (open-source, 95K+ stars, multi-model)
2. **Aider** (open-source, git-native, map-based context)
3. **Claude Code** (free tier, agentic, terminal-native)
4. **GitHub Copilot CLI** (free tier, 2K completions/month)
5. **Continue** (open-source, IDE + terminal, any model)

For each tool, evaluate:
- Context handling (how well it understands my codebase)
- Free tier limits (tokens, requests, features)
- Setup complexity (1-5, where 1 = one command)
- Best for (specific scenarios where it wins)
- Dealbreakers (when NOT to use it)

Then give me:
1. **Your pick** for my specific setup (with reasoning)
2. **Runner-up** (and when I'd switch to it)
3. **Setup commands** to get started in under 2 minutes
4. **Power tip** that most people miss with the chosen tool

Be opinionated. I want a decision, not a fence-sit.
```

## When to Use

- Starting a new project and choosing your AI coding assistant
- Evaluating whether to switch from a paid tool
- Setting up a team's free AI coding stack

## Example Output

The prompt generates a personalized recommendation with install commands, configuration, and a "power tip" specific to your setup.

## Tips

- OpenCode shines for multi-model flexibility (use different LLMs per task)
- Aider's repo-map gives best context for large codebases
- Claude Code free tier is limited but has the best agentic capabilities
- Combine tools: use Aider for commits + OpenCode for exploration

---

> 💡 **Want the full version?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes 100+ production-ready resources including a complete AI Coding CLI Mastery system with multi-tool orchestration configs, shell aliases, git hooks, CI/CD integration, and cost optimization for mixing free + paid tiers.
