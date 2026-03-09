# 🚀 The Learning Accelerator

> **When to use:** You need to learn a new technology fast — for a job, project, or interview.

## Prompt Template

```
I need to learn [technology/concept] quickly.

Context:
- I already know: [related technologies you know]
- I need it for: [job interview / new project / curiosity]
- Timeline: [how much time I have]
- Learning style: [examples-first / theory-first / project-based]

Create a learning plan:
1. Core concepts I must understand (ordered by importance)
2. The "20% that gives 80% of value"
3. Hands-on exercises for each concept (progressively harder)
4. Common mistakes beginners make (so I can skip them)
5. Resources: 1 video, 1 article, 1 interactive tutorial
6. A "build this" project to cement the knowledge
```

## Example Output

**Input:** "I need to learn Docker in 3 days. I know Linux basics."

> **Day 1: Core concepts (2 hours)**
> - Container vs VM (it's a process, not a machine)
> - Image vs Container (class vs instance)
> - Hands-on: `docker run -it ubuntu bash` → explore, then `exit`
>
> **Day 2: Build things (3 hours)**
> - Write a Dockerfile for a Node.js app
> - Docker Compose for app + database
> - Volumes for persistent data
>
> **Day 3: Production skills (2 hours)**
> - Multi-stage builds, health checks, Docker networking
>
> **Common mistakes:** Don't run as root. Don't use `latest` tag. Don't put secrets in Dockerfiles.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
