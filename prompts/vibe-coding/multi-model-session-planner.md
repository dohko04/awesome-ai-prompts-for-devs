# 🎯 Multi-Model Vibe Coding Session Planner

> Plan your coding session strategically across multiple AI models. Know when to use GPT-4.1/GPT-5 for reasoning, Claude for code generation, Gemini for large context, and local models for speed. Stop wasting tokens on the wrong model.

## The Prompt

```markdown
You are a senior developer who has mastered multi-model AI-assisted coding. Help me plan my coding session by assigning the right AI model to each task based on its strengths.

## My Available Models
[List your models, e.g.:]
- Claude 3.5/4 (via Cursor / Claude Code)
- GPT-4.1 / GPT-5 (via Copilot / API)
- Gemini 2.5 Pro (large context window)
- Local model via Ollama (fast, private, no token cost)

## My Project
- **Stack:** [your tech stack]
- **Codebase size:** [small <5k LOC | medium 5-50k | large 50k+]
- **Today's tasks:** [list what you want to accomplish]

## Create a Session Plan With:

### Task → Model Assignment
For each task I listed, recommend which model to use and why:

| Task | Best Model | Why | Mode |
|------|-----------|-----|------|
| [task] | [model] | [reasoning] | [autocomplete / agent / chat] |

### Model Selection Rules
Apply these heuristics:
- **Large refactors across many files** → Agent mode with Claude (best at following complex instructions across files)
- **Quick completions while typing** → Local model or Copilot (lowest latency, no cost)
- **Understanding a huge codebase** → Gemini 2.5 Pro (1M+ token context)
- **Complex architecture decisions** → GPT-5 or Claude in chat mode (strong reasoning)
- **Writing tests** → Any agent mode (tests are well-defined, predictable)
- **Debugging with stack traces** → Claude or GPT-4.1 (strong at error analysis)
- **Sensitive/proprietary code** → Local model ONLY (no data leaves your machine)

### Cost Optimization
- Estimate token usage per task
- Suggest where to use local models to save money
- Flag tasks where premium models are overkill

### Context Strategy
- Which files to load into context for each task
- When to use @-mentions vs. full codebase indexing
- How to structure .cursorrules or CLAUDE.md for each task type

### Session Flow
Give me an ordered schedule:
1. Start with [task] using [model] because...
2. Then switch to [task] using [model]...
3. ...

Optimize for flow state — minimize model switching, batch similar tasks.
```

## When to Use

- At the start of any serious coding session (15+ minutes)
- When you have access to multiple AI tools and don't know which to pick
- Before burning $20 in API tokens on tasks a local model could handle
- When onboarding to a new codebase and need to strategize your approach

## Pro Tips

- **Latency kills flow** — use local models for autocomplete, save cloud models for complex tasks
- **Context is king** — Gemini's 1M token window is unbeatable for "read this entire codebase" tasks
- **Agent mode ≠ always better** — for quick edits, autocomplete is 10x faster than waiting for an agent
- In 2026, the best devs aren't loyal to one tool — they orchestrate multiple models like instruments

## Real-World Example

```
Session: Building a new API endpoint with tests

1. 🧠 Architecture chat (5 min) → Claude chat: "Design the endpoint, suggest patterns"
2. 🏗️ Scaffold code (10 min) → Claude agent: Generate route, controller, types
3. ⚡ Write implementation (20 min) → Copilot autocomplete: Fast typing with suggestions
4. 🧪 Generate tests (10 min) → Claude agent: "Write tests for this endpoint"
5. 🐛 Debug failures (5 min) → GPT-4.1 chat: Paste error, get fix
6. 📝 Documentation (5 min) → Local model: Generate JSDoc comments (free)
```

---

> 💡 **Want model-specific prompt templates for Cursor, Claude Code, Copilot, and Windsurf?** The full toolkit has optimized prompts for each tool.
>
> **[Get 100+ prompts like this → AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)**
