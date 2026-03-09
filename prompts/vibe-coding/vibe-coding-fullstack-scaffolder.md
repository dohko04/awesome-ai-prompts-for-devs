# 🎸 Vibe Coding Full-Stack Scaffolder

Go from idea to deployed app using natural language. The hottest trend in 2026 — 41% of code is now AI-generated. This prompt turns you into an AI orchestrator, not a typist.

## The Prompt

```
You are a Vibe Coding Architect. I want to build an app using natural language and AI tools. Help me scaffold the entire project from a single description.

My app idea: {APP_DESCRIPTION}

Follow this process:

1. **Tech Stack Decision**: Based on my description, recommend:
   - Frontend framework (Next.js, Nuxt, SvelteKit, etc.)
   - Backend/API approach (serverless, Express, tRPC, etc.)
   - Database (Postgres, SQLite, Supabase, etc.)
   - Deployment target (Vercel, Railway, Fly.io, etc.)
   - Justify each choice in one sentence

2. **Project Structure**: Output the complete folder structure with:
   - All directories and key files
   - Brief comment for each file's purpose
   - Which files the AI should generate first (priority order)

3. **AI-First Development Rules**: Generate a `.cursorrules` or `AGENTS.md` file that:
   - Defines coding standards for the AI assistant
   - Sets boundaries (what the AI should/shouldn't do)
   - Includes project context so the AI understands the domain
   - Specifies testing and error handling conventions

4. **Implementation Prompts**: Give me 5 copy-paste prompts I can feed to Cursor/Claude Code/Copilot to build each layer:
   - Data models and database schema
   - API routes with validation
   - UI components with styling
   - Authentication flow
   - Deployment config

5. **Vibe Check Checklist**: A pre-launch checklist to verify:
   - [ ] All routes work
   - [ ] Auth is secure
   - [ ] Environment variables are set
   - [ ] Error handling exists
   - [ ] Basic tests pass

Output everything in markdown I can copy directly into my project.
```

## Example Usage

> "I want a SaaS dashboard where users can connect their GitHub repos and see AI-generated code quality reports with charts"

## When to Use

- Starting a new project with AI coding tools (Cursor, Claude Code, Copilot, Windsurf)
- You have an idea but don't want to spend hours on boilerplate
- You want a structured approach to vibe coding instead of chaos

## Pro Tips

- Paste the generated `AGENTS.md` into your repo root — it dramatically improves AI code quality
- Use the implementation prompts in order for best results
- Iterate on each layer before moving to the next

---

> 💡 **Want more?** This is 1 of 8 vibe coding prompts in the free collection. The [**Full AI Dev Toolkit**](https://ai-dev-toolkit-five.vercel.app) includes 20+ vibe coding workflows with advanced scaffolding, multi-agent development loops, and production deployment pipelines — all for **$9 USD**.
