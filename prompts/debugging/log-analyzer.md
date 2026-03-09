# 📋 The Log Analyzer

> **When to use:** You have a wall of logs and need to find the needle in the haystack.

## Prompt Template

```
Analyze these application logs and find the problem:

[paste logs - up to 200 lines]

Context:
- The issue is: [describe the symptom]
- This started: [when it began]

Please:
1. Identify the first error/warning that matters
2. Trace the chain of events that led to the failure
3. Ignore noise — focus only on what's relevant
4. Suggest the fix
```

## Example Output

> **Key finding:** Line 47 shows `Connection pool exhausted` at 14:32:01, followed by cascading timeout errors.
>
> **Chain of events:**
> 1. 14:31:45 — Slow query on `users` table (took 12s instead of <100ms)
> 2. 14:31:50 — Connection pool filled up waiting for that query
> 3. 14:32:01 — New requests can't get connections → pool exhausted
> 4. 14:32:01+ — All subsequent requests fail with timeouts
>
> **Fix:** Add a query timeout (`statement_timeout = 5000`) and investigate the slow query with `EXPLAIN ANALYZE`.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
