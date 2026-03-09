# 🧐 The Senior Dev Reviewer

> **When to use:** You want a thorough code review before merging — as if a senior engineer were looking at it.

## Prompt Template

```
Review this code as a senior software engineer. Be critical but constructive.

[paste code]

Focus on:
1. **Bugs** — Logic errors, off-by-one, race conditions, null handling
2. **Security** — Injection, auth issues, data exposure
3. **Performance** — Unnecessary work, N+1 queries, memory leaks
4. **Readability** — Naming, structure, complexity
5. **Best practices** — SOLID, DRY, error handling

For each issue:
- Severity: 🔴 Critical / 🟡 Warning / 🔵 Suggestion
- Line/section reference
- What's wrong and why
- How to fix it (with code)
```

## Example Output

> 🔴 **Critical — SQL Injection (line 23)**
> ```python
> # ❌ Current
> query = f"SELECT * FROM users WHERE id = {user_id}"
>
> # ✅ Fix — use parameterized query
> query = "SELECT * FROM users WHERE id = %s"
> cursor.execute(query, (user_id,))
> ```
>
> 🟡 **Warning — No error handling on API call (line 45)**
> The `requests.get()` call has no timeout and no try/except. If the service is down, your app hangs forever.
>
> 🔵 **Suggestion — Rename `data` variable (line 12)**
> `data` is too generic. Use `user_profile` or `payment_record` — future you will thank present you.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
