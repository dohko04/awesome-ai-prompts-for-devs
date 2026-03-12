# Goose AI Coding Agent — Free Claude Code Alternative Setup

> Goose by Block (formerly Square) is an open-source AI coding agent that runs locally. It does what Claude Code does — but free. This prompt helps you set it up properly and get productive fast.

## The Prompt

```
You are my AI setup assistant. I want to configure Goose (Block's open-source AI coding agent) as my primary coding tool — a free alternative to Claude Code.

MY SETUP:
- OS: [macOS/Linux/Windows WSL]
- Primary language: [e.g., TypeScript, Python, Rust]
- Project type: [e.g., web app, CLI tool, API service]
- Current AI tool: [what I'm migrating from, if any]
- LLM provider I want to use: [OpenAI/Anthropic/Ollama local/other]

Help me with:

1. INSTALLATION
   - Step-by-step install for my OS
   - Required dependencies
   - Shell/terminal configuration

2. LLM PROVIDER CONFIG
   - How to connect my preferred LLM provider
   - API key setup (environment variables)
   - If I want FREE: how to use Ollama + a local model as backend
   - Model selection: which model works best with Goose for coding

3. PROJECT SETUP
   - How to initialize Goose in my project directory
   - Creating effective .goosehints files (like .cursorrules)
   - Setting up context boundaries so Goose understands my codebase

4. FIRST PRODUCTIVE SESSION
   - 5 real commands I should try first for my project type
   - Common pitfalls and how to avoid them
   - How Goose handles file editing vs Claude Code

5. WORKFLOW COMPARISON
   - What Goose does BETTER than Claude Code
   - What Goose does WORSE (so I know when to switch)
   - Token/cost comparison for my usage pattern

Format as a step-by-step guide I can follow in one sitting.
```

## Example Use Cases

**Migrating from Claude Code ($200/mo) to Goose (free):**
```
MY SETUP:
- OS: macOS
- Primary language: TypeScript
- Project type: Next.js web app
- Current AI tool: Claude Code (want to reduce costs)
- LLM provider: Anthropic API (pay-per-token, cheaper than subscription)
```

**Fully local/offline setup:**
```
MY SETUP:
- OS: Linux
- Primary language: Python
- Project type: ML pipeline
- Current AI tool: None
- LLM provider: Ollama with Qwen 3.5 or NousCoder-14B (fully free & local)
```

## Why Goose?

- **$0/month** — open source, runs locally
- Built by **Block** (Jack Dorsey's fintech company) — serious engineering
- Works with **any LLM provider** — OpenAI, Anthropic, Ollama, etc.
- **13,100+ commits**, actively maintained as of March 2026
- Terminal-native like Claude Code — similar UX, no IDE lock-in

## Quick Install Cheatsheet

```bash
# macOS
brew install goose

# Or from source (any OS)
cargo install goose-cli

# Verify
goose --version
```

---

> 💡 **Want the full Goose workflow?** The [AI Dev Toolkit](https://dohko04.gumroad.com/l/ai-dev-toolkit) ($9) includes a complete Goose Production Workflow with `.goosehints` templates for 8 project types, cost optimization strategies, multi-model routing, and team rollout guides.
