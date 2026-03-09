# Claude Code Project Setup Generator (Free)

> Generate a complete CLAUDE.md + custom commands setup for any project. This is the #1 thing every dev needs for effective vibe coding in 2026.

## The Prompt

```
You are a Claude Code project configuration expert. I need you to generate a complete project setup for Claude Code based on my project details.

PROJECT: {{project_description}}
TECH STACK: {{tech_stack}}
REPO STRUCTURE: {{repo_structure}}

Generate the following:

## 1. CLAUDE.md (project instructions file)
Create a CLAUDE.md that includes:
- Project overview and architecture
- Key conventions (naming, file structure, patterns)
- Common commands (build, test, lint, deploy)
- Important files and their purposes
- Things Claude should NEVER do (destructive operations, etc.)
- Testing requirements before committing

## 2. Two custom slash commands
For each command provide:
- Filename (e.g., `.claude/commands/review.md`)
- The prompt template with $ARGUMENTS placeholder
- Example usage

Focus on the two most impactful commands for this specific project type.
```

## Example Output

For a Next.js SaaS app, this generates:
- A CLAUDE.md with App Router conventions, environment setup, and safety rules
- `/review` command for PR-style code review
- `/feature` command for scaffolding new features with tests

---

> 🔥 **Want the full version?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) ($9) includes:
> - 8 pre-built command templates (review, refactor, test, deploy, debug, migrate, document, security-audit)
> - CLAUDE.md templates for 12 project types (Next.js, FastAPI, Go, Rust, mobile, monorepo...)
> - .cursorrules and .windsurfrules generators
> - Cursor Composer workflow prompts
> - Complete vibe coding playbook with advanced patterns
