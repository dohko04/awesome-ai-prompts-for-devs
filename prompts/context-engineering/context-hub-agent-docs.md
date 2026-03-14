# Context Hub — Feed Curated Docs to Your Coding Agent

> Give your AI coding agent the right API documentation so it writes correct code, not hallucinated garbage.

## The Problem

Coding agents (Claude Code, Cursor, Copilot) hallucinate API calls because they don't have access to current documentation. Context Hub (by Andrew Ng) solves this with a CLI that serves curated, versioned docs to your agent.

## Quick Setup

```bash
# Install Context Hub
pip install context-hub

# Initialize in your project
cd your-project
context-hub init

# Add API docs your agent needs
context-hub add openai --version latest
context-hub add stripe --version 2026-02-24
context-hub add supabase --version 2.x
```

## Basic Usage with Claude Code

```bash
# Generate context file for your agent
context-hub generate --output .context/apis.md

# Reference in your CLAUDE.md or .cursorrules
echo "Read .context/apis.md before writing any API integration code." >> CLAUDE.md
```

## Starter .context-hub.yaml

```yaml
# .context-hub.yaml — put this in your project root
version: 1
sources:
  - name: openai
    type: api-reference
    url: https://platform.openai.com/docs/api-reference
    sections:
      - chat-completions
      - embeddings
      - assistants
    version: latest

  - name: project-api
    type: local
    path: ./docs/api-spec.yaml
    format: openapi

rules:
  - "Always check context docs before generating API calls"
  - "If an API is not in context, ask the user — don't guess"
```

## Example: Before vs After

**Without Context Hub** (agent hallucinates):
```python
# Agent generates this — WRONG, uses deprecated endpoint
response = openai.Completion.create(model="text-davinci-003", prompt="...")
```

**With Context Hub** (agent uses correct docs):
```python
# Agent generates this — CORRECT, uses current API
response = openai.chat.completions.create(
    model="gpt-5.4",
    messages=[{"role": "user", "content": "..."}]
)
```

## When to Use This

- ✅ Multi-API projects (3+ external services)
- ✅ Fast-moving APIs that change frequently
- ✅ Team projects where agents need consistent context
- ✅ Any project where your agent keeps hallucinating API calls

---

> 🔥 **Want the full production pipeline?** The [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) includes a complete Context Hub orchestration system with multi-agent doc routing, auto-versioning, freshness checks, and CI/CD integration for keeping agent context always current.
