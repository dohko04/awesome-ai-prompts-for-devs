# OpenAI Codex Multi-Project Manager

> **Category:** Vibe Coding · **Difficulty:** Intermediate · **Updated:** March 2026

OpenAI Codex now supports parallel project threads and deep personalization. This prompt helps you set up an efficient multi-repo workflow with custom configurations per project.

## The Prompt

```
You are a Codex Workspace Architect. Help me configure OpenAI Codex for managing
multiple projects simultaneously with optimal settings per project type.

For each project I give you, generate:

1. **Project Profile** — a Codex configuration block:
   - Language/framework detection
   - File handling rules (which files to index, which to ignore)
   - Code style preferences (formatting, naming conventions)
   - Integration settings (Git, CI/CD, testing framework)

2. **Context Strategy** — how Codex should understand this project:
   - Key files to always keep in context
   - Architecture patterns to recognize
   - Domain-specific terminology glossary
   - Common task patterns (e.g., "new endpoint" → controller + service + test + migration)

3. **Thread Organization** — parallel task management:
   - Naming convention for task threads
   - Priority system (P0 = blocking, P1 = today, P2 = this week)
   - Cross-project dependency flags

My projects:
- Project 1: [NAME] — [TECH_STACK] — [DESCRIPTION]
- Project 2: [NAME] — [TECH_STACK] — [DESCRIPTION]
- Project 3: [NAME] — [TECH_STACK] — [DESCRIPTION]
```

## How to Use

1. Open Codex → Settings → enable multi-project mode
2. Paste this prompt with your actual projects
3. Apply each generated configuration to the corresponding project
4. Use thread naming conventions to keep tasks organized
5. Review cross-project dependencies weekly

## Example Configuration

```yaml
# Project: api-backend
codex_profile:
  language: Python 3.12
  framework: FastAPI
  style:
    formatter: ruff
    naming: snake_case
    docstrings: google
  context:
    always_include:
      - src/core/models.py
      - src/api/routes/__init__.py
      - tests/conftest.py
    ignore:
      - "*.pyc"
      - ".venv/"
      - "migrations/versions/"
  tasks:
    new_endpoint: "route + service + schema + test + migration"
    bug_fix: "reproduce test → fix → verify"
```

## Why This Matters

Devs juggling 2-3 projects waste ~30 min/day context-switching. With Codex's new multi-project support, you can maintain separate AI contexts per project — but only if you configure them properly. This prompt generates production-ready configs.

---

> 🔒 **Want the full Multi-Project Pipeline?** The PRO version includes 8 project-type templates (API, frontend, CLI, ML, mobile, infra, monorepo, library), automated context refresh, cross-project dependency tracking, and team-shared configurations → [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)
