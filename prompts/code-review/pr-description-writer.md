# 📝 The PR Description Writer

> **When to use:** You've made changes and need a clear, professional pull request description.

## Prompt Template

```
Write a PR description for these changes:

**Diff/Changes:**
[paste git diff or describe the changes]

**Context:**
- Why: [reason for the change]
- Ticket: [JIRA/Linear ID if applicable]

Generate:
1. A clear title (conventional commits format)
2. Summary of what changed and why
3. How to test it
4. Any risks or things reviewers should watch for
5. Screenshots section placeholder (if UI changes)
```

## Example Output

> **Title:** `feat(auth): add rate limiting to login endpoint`
>
> **Summary:** Adds rate limiting (5 attempts/minute per IP) to the `/auth/login` endpoint to prevent brute-force attacks. Uses Redis sliding window counter.
>
> **How to test:**
> 1. Hit `/auth/login` with wrong credentials 6 times in 1 minute
> 2. Verify 6th attempt returns `429 Too Many Requests`
> 3. Wait 60 seconds, verify you can try again
>
> **Risks:** If Redis goes down, rate limiting fails open (allows all requests). Acceptable for now, tracked in PROJ-456.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
