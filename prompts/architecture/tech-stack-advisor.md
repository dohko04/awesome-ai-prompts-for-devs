# 🧭 The Tech Stack Advisor

> **When to use:** You're starting a project and need to choose the right tools for the job.

## Prompt Template

```
I'm building: [describe the project]

Context:
- Team size: [number and skill level]
- Timeline: [deadline]
- Budget: [infrastructure budget]
- Must integrate with: [existing systems]
- Users: [expected traffic/load]

For each layer (frontend, backend, database, hosting, CI/CD), recommend:
1. Your top pick and WHY (not just what)
2. A runner-up alternative
3. What NOT to use and why
4. Monthly cost estimate at my scale
```

## Example Output

> **Backend layer:**
>
> **Top pick: Node.js + Fastify**
> Why: Your team knows JS, 2-week timeline is tight, and Fastify is 2x faster than Express with similar DX.
>
> **Runner-up: Python + FastAPI**
> Why: Better if you need ML/data integration later.
>
> **Avoid: Java Spring Boot**
> Why: Massive overkill for a 3-person team with a 2-week deadline.
>
> **Cost:** ~$7/mo on Railway (hobby) → ~$25/mo on Render (pro) at 10K users.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
