# 🧩 Agent Skills Registry Starter (skills.sh)

> Install reusable AI agent skills across Claude Code, Cursor, Copilot, and 30+ agents. The "npm for AI agents" workflow.

## The Prompt

```markdown
You are an AI Agent Skills architect. Help me set up and use reusable agent skills using the skills.sh ecosystem (Vercel's open registry) and Anthropic's official skills.

## Context
- skills.sh is an open registry for agent skills (like npm for AI behaviors)
- Skills are SKILL.md files with YAML frontmatter + supporting assets
- Works with: Claude Code, Cursor, GitHub Copilot, Aider, Codex, Gemini
- Install: `npx skills add <skill-name>`
- Official Anthropic skills: github.com/anthropics/skills

## Task
For my project: [DESCRIBE YOUR PROJECT]

1. **Discover** — Search skills.sh for skills relevant to my stack
2. **Install** — Set up the top 3 most useful skills for my workflow
3. **Configure** — Show the directory structure after installation:
   - `.claude/skills/` for Claude Code
   - `.cursor/skills/` for Cursor
4. **Verify** — Test each skill works with a sample task

## Skill Structure Reference
```
my-skill/
├── SKILL.md        # Required — instructions + YAML frontmatter
├── templates/      # Optional supporting files
├── examples/       # Example outputs
└── scripts/        # Executable scripts
```

## Output Format
For each recommended skill:
- **Name**: skill identifier
- **What it does**: one-line description
- **Install command**: exact CLI command
- **Test task**: a quick way to verify it works
- **Why it helps**: concrete benefit for my project
```

## Example Use Cases

- **Full-stack dev**: Install skills for React, API design, and testing
- **DevOps**: Install skills for Terraform, Docker, and CI/CD
- **Data engineer**: Install skills for SQL optimization, ETL, and dbt

## What You Get (Free)

✅ Discover and install skills from the registry
✅ Basic skill structure reference
✅ Works with any supported AI agent

## 🔒 Pro Version Includes

The **[AI Dev Toolkit Pro](https://dohko04.github.io/ai-dev-toolkit/)** ($9) includes:

- 🏗️ **Custom skill builder** — Create and publish your own skills to skills.sh
- 📦 **Team skill distribution** — Private registries, versioning, rollback
- 🔄 **Multi-agent skill sync** — Same skills across Claude, Cursor, Copilot simultaneously
- 📊 **Skill performance tracker** — Measure which skills actually improve your output
- 🧪 **Skill testing framework** — Validate skills before deploying to your team

---

*Part of [awesome-ai-prompts-for-devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — Production-ready AI prompts for developers*
