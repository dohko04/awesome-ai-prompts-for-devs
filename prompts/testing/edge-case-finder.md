# 🎯 The Edge Case Finder

> **When to use:** You think your code works but want to know what you're missing.

## Prompt Template

```
Find edge cases and potential failures in this code:

[paste code]

Think about:
- Boundary values (0, -1, MAX_INT, empty string, null)
- Concurrency issues (race conditions, deadlocks)
- Network failures (timeouts, partial responses)
- Malicious input (injection, overflow)
- State issues (uninitialized, stale, corrupt)
- Platform differences (timezone, locale, OS)

For each edge case:
1. Describe the scenario
2. What happens currently (crash? wrong result? silent failure?)
3. How to handle it properly
```

## Example Output

**Input:** A function that parses user-uploaded CSV files.

> **Edge case 1: Empty file**
> Currently: Throws `index out of range` on line 12. Fix: Check `if len(rows) == 0: return []`
>
> **Edge case 2: CSV with 1 million rows**
> Currently: Loads entire file into memory → OOM crash. Fix: Use streaming/chunked reader.
>
> **Edge case 3: Fields containing commas or newlines**
> Currently: Breaks parsing. Fix: Use a proper CSV library instead of `.split(',')`.
>
> **Edge case 4: BOM character in UTF-8 file (common from Excel)**
> Currently: First column header has invisible `\ufeff` prefix → column lookup fails silently.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
