# Astral + Codex Python Migration Starter (FREE)

> OpenAI acquired Astral (uv, Ruff, ty) on March 19, 2026. Python tooling is merging with AI coding. Get your project ready.

## Quick Migration Checklist

```markdown
## Astral Tool Adoption Checklist

### Step 1: Install Astral Tools
- [ ] Install uv: `curl -LsSf https://astral.sh/uv/install.sh | sh`
- [ ] Verify: `uv --version` (should be 0.6+)
- [ ] Ruff comes with uv: `uv tool install ruff`
- [ ] ty (type checker): `uv tool install ty`

### Step 2: Migrate Dependencies
- [ ] From pip: `uv init && uv add $(cat requirements.txt | grep -v "^#" | tr '\n' ' ')`
- [ ] From poetry: `uv init && uv sync` (reads pyproject.toml)
- [ ] Verify: `uv sync --frozen`

### Step 3: Replace Linting/Formatting
- [ ] Remove: flake8, black, isort, autopep8, pyflakes
- [ ] Add ruff.toml with your rules
- [ ] Run: `uv run ruff check --fix . && uv run ruff format .`

### Step 4: Replace Type Checking
- [ ] Remove: mypy (optional — can keep alongside)
- [ ] Add [tool.ty] to pyproject.toml
- [ ] Run: `uv run ty check .`

### Step 5: Update CI
- [ ] Replace pip install with: `uv sync --frozen`
- [ ] Replace flake8/black with: `uv run ruff check .`
- [ ] Add: `uv audit` for security scanning
```

## Basic Ruff Config

```toml
# ruff.toml — starter config
target-version = "py312"
line-length = 120
fix = true

[lint]
select = ["E", "F", "W", "I", "UP", "B"]

[format]
docstring-code-format = true
```

## Why Migrate Now?

| Before (pip + flake8 + black + mypy) | After (uv + Ruff + ty) |
|---------------------------------------|------------------------|
| `pip install` — 60-120s | `uv sync` — 1-3s (50x faster) |
| 4 config files | 1 ruff.toml + pyproject.toml |
| Slow CI (lint+format+typecheck = 5min) | Fast CI (all in <30s) |
| No Codex integration | Native Codex AI coding support |

---

🔥 **Want the full pipeline?** The [AI Dev Toolkit PRO ($9)](https://ai-dev-toolkit-five.vercel.app) includes:
- Migration scanner script (analyzes your project automatically)
- Automated uv migration from pip/poetry/conda
- CI/CD pipeline with Codex AI review integration
- Ruff→Codex rule sync engine
- Cost & ROI calculator for team adoption

**230+ production-ready resources** → [ai-dev-toolkit-five.vercel.app](https://ai-dev-toolkit-five.vercel.app)
