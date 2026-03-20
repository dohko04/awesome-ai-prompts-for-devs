# OpenAI × Astral Python Dev Migration Guide (FREE)

> OpenAI acquired Astral (uv, Ruff, ty) on March 19, 2026. This guide helps you prepare your Python projects for the Codex-integrated future.

## What Changed
- **uv** (Python package manager, 10-100x faster than pip) → now part of OpenAI Codex
- **Ruff** (Python linter/formatter, replaces flake8+black+isort) → Codex-native linting
- **ty** (Python type checker) → Codex-native type analysis

## Quick Migration Checklist

```bash
# 1. Install uv (if not already)
curl -LsSf https://astral.sh/uv/install.sh | sh

# 2. Migrate from pip/poetry/pipenv to uv
uv init                          # New project
uv pip compile requirements.in   # From requirements
uv venv && uv pip sync           # Create env + install

# 3. Replace linting stack with Ruff
# Remove: flake8, black, isort, pyflakes, pycodestyle
# Add single tool:
uv pip install ruff
ruff check . --fix               # Lint + autofix
ruff format .                    # Format (replaces black)

# 4. Add ty for type checking
uv pip install ty
ty check .                       # Type check (replaces mypy for speed)
```

## Recommended pyproject.toml

```toml
[project]
name = "my-project"
requires-python = ">=3.11"

[tool.ruff]
target-version = "py311"
line-length = 88

[tool.ruff.lint]
select = ["E", "F", "I", "N", "UP", "S", "B", "A", "C4", "PT"]

[tool.ruff.format]
quote-style = "double"
```

## Why This Matters for AI-Assisted Coding
- Codex will likely auto-lint/format via Ruff natively
- uv's speed means faster CI/CD with AI-generated code
- ty's type inference helps AI models understand your codebase better
- Projects already on Astral tools = zero friction with Codex

## What to Watch
- Codex CLI integration announcements (expected Q2 2026)
- Whether uv becomes the default package manager in Codex sandboxes
- Ruff rule set expansions for AI-generated code patterns

---

> 🔒 **Want the full migration pipeline?** The PRO version includes automated migration scripts, CI/CD templates, team rollout playbook, and Codex optimization configs → [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)
