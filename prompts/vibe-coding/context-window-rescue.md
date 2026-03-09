# 🧠 Context Window Rescue Kit

> When your AI coding session goes off the rails — context bloated, hallucinations creeping in, model confused. This prompt resets and recovers your session without losing progress.

**Works with:** Claude Code, Cursor, Windsurf, Copilot Chat, ChatGPT

## The Problem

Every vibe coder hits this wall: you're 45 minutes into a session, the AI starts suggesting code that contradicts what it wrote 10 minutes ago, or it "forgets" your tech stack. Your context window is full and the model is drowning.

## The Prompt (Free Version)

```markdown
You are a senior developer helping me recover a derailed AI coding session.

## Current Session State
- **Project:** [describe your project in 1-2 sentences]
- **Tech Stack:** [list your stack]
- **What I was building:** [the feature/fix you were working on]
- **What went wrong:** [describe the issue — hallucinations, contradictions, lost context]

## Your Tasks

### 1. Session Audit
Review the conversation so far and identify:
- What was accomplished successfully (keep this)
- Where the AI started going wrong (discard from here)
- Any contradictory suggestions that were applied

### 2. Context Reset Summary
Create a compact summary I can paste into a NEW session that includes:
- Project context (max 5 lines)
- What's already done (file changes, completed work)
- What still needs to happen
- Key constraints the AI must follow

### 3. Recovery Checklist
- [ ] Files that need to be reverted
- [ ] Code that was correctly generated (keep)
- [ ] The exact next step to resume from

Format the Context Reset Summary as a copy-paste ready prompt I can use immediately.
```

## Usage Tips

1. **Paste this prompt** when you notice the AI getting confused
2. **Copy the generated summary** into a fresh session
3. **Start clean** with compressed, high-quality context

## When to Use This

- AI starts contradicting itself
- Suggestions stop matching your tech stack
- You're 30+ minutes into a session and quality drops
- The AI "forgets" decisions made earlier
- Error loops: the fix creates a new bug, fix creates another bug

## Example Context Reset Output

The prompt will generate something like:

```markdown
## Session Context (paste into new chat)

Project: E-commerce API in Node.js/Express + PostgreSQL + Prisma
Auth: JWT with refresh tokens (DONE, working)
Current task: Shopping cart endpoint - PATCH /cart/:id

### Completed:
- Cart model in Prisma schema ✅
- POST /cart endpoint ✅  
- GET /cart/:userId endpoint ✅

### Resume from:
Implement PATCH /cart/:id with quantity validation (min: 1, max: 99)
Use the same error handling pattern as POST /cart (see src/routes/cart.ts)

### Constraints:
- All routes need auth middleware
- Use Zod for input validation (already set up)
- Follow existing error response format: { error: string, code: number }
```

---

## 🚀 Full Toolkit Version

The complete **Context Window Rescue Kit** in the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes:

- **Auto-detect context degradation** — prompt that monitors AI response quality
- **Multi-file session splitter** — break large tasks into context-safe chunks  
- **Session handoff template** — transfer context between different AI tools (Cursor → Claude Code → ChatGPT)
- **Project memory file generator** — create `.ai-context` files that persist across sessions
- **Emergency rollback prompt** — when the AI has made 5+ files of bad changes
- Plus **6 more context management prompts** for advanced workflows

[**Get the Full Toolkit (100+ prompts) → $9**](https://ai-dev-toolkit-five.vercel.app)

---

*Part of [Awesome AI Prompts for Devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) by [Dohko](https://github.com/dohko04)*
