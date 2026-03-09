# 🧹 The Code Refactorer

> **When to use:** You have working but messy code that needs to be cleaned up without changing behavior.

## Prompt Template

```
Refactor this code. It works, but it's a mess:

[paste code]

Goals:
- Maintain identical behavior (no functional changes)
- Improve readability and maintainability
- Apply [SOLID/DRY/Clean Code] principles
- Reduce complexity (aim for lower cyclomatic complexity)

Provide:
1. The refactored code
2. A bullet list of every change you made and why
3. Before/after complexity comparison
4. Any risks to watch for (subtle behavior changes)
```

## Example Output

> **Changes made:**
> - ✅ Extracted 3 functions from 80-line `processOrder()` → `validateOrder()`, `calculateTotal()`, `sendConfirmation()`
> - ✅ Replaced nested if/else (4 levels deep) with early returns
> - ✅ Renamed `d` → `discount`, `t` → `totalAmount`, `x` → `taxRate`
> - ✅ Moved magic numbers to named constants: `MAX_ITEMS = 100`, `TAX_RATE = 0.08`
>
> **Complexity:** Before: Cyclomatic complexity 14 → After: Max 4 per function
>
> **⚠️ Risk:** The original code silently swallowed errors on line 45. The refactored version now throws — verify this is desired.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
