# 🔓 The Error Message Decoder

> **When to use:** You get a cryptic error message and need to understand what it actually means.

## Prompt Template

```
I'm getting this error and I don't understand it:

Error: [paste the full error message/stack trace]

Context:
- Language/Framework: [e.g., Python 3.11, React 18]
- What I was doing: [action that triggered it]
- Recent changes: [what changed before the error appeared]

Please:
1. Explain this error in plain English
2. List the top 3 most common causes
3. Show me how to fix each cause
4. Give me a diagnostic command/snippet to pinpoint which cause it is
```

## Example Output

**Input:** `ECONNREFUSED 127.0.0.1:5432` in a Node.js app.

**Output:**

> **Plain English:** Your app tried to connect to PostgreSQL on localhost port 5432, but nothing is listening there.
>
> **Top 3 causes:**
> 1. PostgreSQL isn't running → `sudo systemctl start postgresql`
> 2. It's running on a different port → check `postgresql.conf` for `port =`
> 3. You're in Docker and `localhost` means the container, not the host → use `host.docker.internal` or the service name
>
> **Diagnostic:** `pg_isready -h 127.0.0.1 -p 5432`

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
