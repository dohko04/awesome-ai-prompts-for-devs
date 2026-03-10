# 🎸 Agent Skills Setup for Coding Assistants

> **Trending:** The Agent Skills standard is exploding (March 2026). Claude Code, Cursor, Copilot, and Gemini CLI all support skills that supercharge your AI coding workflow. This prompt helps you configure the perfect skill stack.

## The Prompt (Free Version)

```
You are an expert in AI coding agent configuration. Help me set up the optimal agent skills stack for my project.

My setup:
- Editor/Tool: [Claude Code / Cursor / Copilot / Gemini CLI]
- Project type: [web app / API / CLI / mobile / infra]
- Stack: [e.g., TypeScript, Next.js, Postgres, Docker]
- Team size: [solo / small team / enterprise]

Generate:
1. **Recommended skills to install** — list each skill with its install command and what it does
2. **AGENTS.md file** — project-level agent instructions file with:
   - Project context and architecture overview
   - Coding conventions and patterns to follow
   - Files/folders the agent should know about
   - Common tasks and how to approach them
3. **.cursorrules or .claude/settings.json** — tool-specific config
4. **Workflow tips** — 5 power-user patterns for this specific stack

Format the output as copy-paste ready files I can drop into my repo.
```

## Example Skills

```bash
# Popular skills to install (March 2026)
npx skills add @anthropic/code-review    # PR review automation
npx skills add @pulumi/infra             # Infrastructure as code
npx skills add @vercel/nextjs            # Next.js best practices
npx skills add @prisma/database          # Database workflows
```

---

## 🚀 Want the Full Version?

The **[AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)** includes:
- ✅ Complete AGENTS.md templates for 10+ project types
- ✅ Pre-built skill configurations for every major framework
- ✅ Multi-agent workflow setups (architect + coder + reviewer)
- ✅ Custom skill creation guide
- ✅ 100+ battle-tested prompts for every dev workflow

[**Get the Full Toolkit →**](https://ai-dev-toolkit-five.vercel.app)
