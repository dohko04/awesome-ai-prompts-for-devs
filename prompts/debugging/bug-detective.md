# 🔍 The Bug Detective

> **When to use:** You have a bug and need systematic root-cause analysis instead of guessing.

## Prompt Template

```
I have a bug. Here's what I know:

**Expected behavior:** [what should happen]
**Actual behavior:** [what happens instead]
**Reproduction steps:** [how to trigger it]

Code:
[relevant code]

Error output (if any):
[errors/logs]

Help me:
1. Identify the most likely root cause
2. Explain WHY it's happening (not just what)
3. Provide the fix with code
4. Suggest how to prevent similar bugs in the future
```

## Example Output

**Input:** A React component re-renders infinitely when using `useEffect` with an object dependency.

**Output:**

> **Root cause:** You're passing an object literal as a dependency to `useEffect`. On every render, JavaScript creates a new object reference, so React thinks the dependency changed → triggers re-render → new object → infinite loop.
>
> **Fix:**
> ```javascript
> // ❌ Bad - new object reference every render
> useEffect(() => { fetchData(filters) }, [{ status: 'active', page: 1 }]);
>
> // ✅ Good - stable reference with useMemo
> const filters = useMemo(() => ({ status: 'active', page: 1 }), []);
> useEffect(() => { fetchData(filters) }, [filters]);
> ```
>
> **Prevention:** Use the `react-hooks/exhaustive-deps` ESLint rule and never pass inline objects/arrays as dependencies.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
