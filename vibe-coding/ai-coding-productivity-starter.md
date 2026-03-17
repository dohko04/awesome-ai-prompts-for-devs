# AI Coding Productivity Multiplier — Starter

> Turn AI coding tools into a 2x productivity engine. Based on March 17, 2026 data: top AI adopters ship nearly double the pull requests weekly with no quality drop.

## The Key Insight

It's NOT about typing faster. The 2x comes from **eliminating wait states**:
- Context loading → AI pre-warms your codebase understanding
- Boilerplate writing → AI scaffolds in seconds
- PR descriptions → AI generates from diff
- Code review cycles → AI pre-reviews before humans

## Task-to-Tool Quick Router

| Task | Best Tool | Why |
|------|-----------|-----|
| New feature | Cursor Agent | Multi-file scaffolding |
| Bug fix | Copilot Inline | Fast, context-aware |
| Refactor | Claude Code | Best reasoning |
| Tests | Copilot /tests | Excellent test generation |
| PR description | Claude Code | Summarizes diffs well |
| Code review | Claude Code | Finds logic issues |

## Daily Routine (5-min Setup = 60-min Saved)

```bash
# 1. Start of day: create focus file
cat > .cursor/today.md << 'EOF'
# Today's Focus (max 3 items)
1. [ ] [your task 1]
2. [ ] [your task 2]  
3. [ ] [your task 3]

## Context for AI
- Working on: [feature/area]
- Key files: [list main files]
EOF

# 2. Pre-warm AI context
# In Cursor: @codebase explain the architecture in src/

# 3. Check yesterday's output
git log --since="1 day ago" --oneline
```

## 3 Rules for 2x Output

1. **Right tool for right task** — Don't use Cursor for simple fixes, don't use Copilot for architecture
2. **Batch AI interactions** — Ask 3 things at once, not 3 separate prompts
3. **AI for the boring 80%, you for the critical 20%** — CRUD/boilerplate/tests = AI. Architecture = you.

---

📊 **Want the full productivity pipeline?** The PRO version includes:
- Automated productivity tracker (Python script for real metrics)
- Cost-optimized tool selection matrix with ROI calculator
- Flow state engineering system (eliminate all wait states)
- 4-week team rollout playbook
- ROI calculator proving 5,000%+ return

→ **[Get the full AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)** — 190+ production-ready resources for $9
