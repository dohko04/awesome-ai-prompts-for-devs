# Gemini 3.1 Pro Developer Workflow

> Quick-start guide to adopt Google's Gemini 3.1 Pro for coding tasks. Launched March 20 2026 with improved reasoning, 2M context window, and availability across AI Studio, Gemini CLI, Antigravity IDE, and Vertex AI.

## Why Gemini 3.1 Pro?

- **2M context window** — Analyze entire codebases in one request
- **$1.25/1M input** — 50% cheaper than GPT-5.4, 92% cheaper than Opus 4.6
- **Improved reasoning** — Significant benchmark gains on complex tasks
- **5 platforms** — AI Studio, CLI, Antigravity, Vertex AI, consumer app

## Basic Setup (Gemini CLI)

```bash
# Install Gemini CLI
npm install -g @google/gemini-cli

# Set your API key
export GOOGLE_API_KEY="your-key-from-aistudio.google.com"

# Start coding with Gemini 3.1 Pro
gemini --model gemini-3.1-pro-preview
```

## Project Configuration

```yaml
# .gemini/config.yaml — Place in project root
model: gemini-3.1-pro-preview
temperature: 0.1

context:
  include:
    - "src/**/*.py"
    - "src/**/*.ts"
    - "tests/**/*"
    - "README.md"
  exclude:
    - "node_modules/**"
    - "dist/**"
    - "*.lock"
```

## Quick Cost Comparison

| Model | Input/1M | Output/1M | Context |
|-------|----------|-----------|---------|
| Gemini 3.1 Pro | $1.25 | $5.00 | 2M |
| GPT-5.4 | $2.50 | $10.00 | 400K |
| GPT-5.4 Mini | $0.75 | $4.50 | 400K |
| Claude Opus 4.6 | $15.00 | $75.00 | 200K |
| Claude Sonnet 4.6 | $3.00 | $15.00 | 1M |

## When to Use Gemini 3.1 Pro

✅ **Best for:** Large codebase analysis, complex reasoning, cost-sensitive teams, agentic workflows
⚠️ **Consider alternatives:** Ultra-low-latency needs (GPT-5.4 Mini), maximum coding quality (Claude Opus 4.6)

---

> 💡 **Want the full production pipeline?** The PRO version includes: multi-provider routing engine, CI/CD quality gates, cost optimization dashboard with SQLite tracking, and Grafana monitoring queries.
>
> **Get the complete AI Dev Toolkit** → [ai-dev-toolkit-five.vercel.app](https://ai-dev-toolkit-five.vercel.app)
