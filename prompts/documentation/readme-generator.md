# 📖 The README Generator

> **When to use:** You need a professional README for your open-source project.

## Prompt Template

```
Generate a comprehensive README.md for my project:

- Project name: [name]
- One-line description: [what it does]
- Tech stack: [languages, frameworks]
- Installation steps: [how to set up locally]
- Main features: [list key features]
- Target audience: [who is this for]

Include:
1. Badges (build status, license, version)
2. Quick start (< 3 minutes to first result)
3. Feature list with brief descriptions
4. Configuration options table
5. FAQ section (3-5 common questions)
6. Contributing section
7. License
```

## Example Output

> ```markdown
> # 🚀 FastQueue
> > A blazing-fast, Redis-backed job queue for Node.js. Process 10K jobs/sec with zero config.
>
> ![npm](https://img.shields.io/npm/v/fastqueue)
> ![build](https://img.shields.io/github/actions/workflow/status/...)
>
> ## Quick Start
> ```bash
> npm install fastqueue
> ```
> ```javascript
> const queue = new FastQueue({ redis: 'redis://localhost' });
> queue.add('email', { to: 'user@example.com' });
> ```
> Done. You're processing jobs. ✅
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
