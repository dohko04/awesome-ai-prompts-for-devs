# 🔑 The Environment & Secrets Checker

> **When to use:** Before deploying, verify you're not leaking secrets or misconfiguring environments.

## Prompt Template

```
Review my project for secrets and configuration security:

Files to check:
[paste .env.example, docker-compose.yml, config files, or describe your setup]

Verify:
1. No hardcoded secrets (API keys, passwords, tokens)
2. .gitignore properly excludes sensitive files
3. Environment variables are validated at startup
4. Secrets rotation strategy exists
5. Different configs for dev/staging/prod
6. No sensitive data in logs or error messages

Provide a security checklist I can run before every deployment.
```

## Example Output

> **Pre-deployment security checklist:**
> - [ ] `git log --all -p | grep -i "password\|secret\|api_key"` → 0 results
> - [ ] `.env` is in `.gitignore` ✅
> - [ ] All secrets come from env vars, not config files ✅
> - [ ] `DATABASE_URL` uses SSL in production (`?sslmode=require`) ❌ **Fix this**
> - [ ] Error responses don't include stack traces in production ✅
> - [ ] CORS is restricted to known domains (not `*`) ❌ **Fix this**

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
