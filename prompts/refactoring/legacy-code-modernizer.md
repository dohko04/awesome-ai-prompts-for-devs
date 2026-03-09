# 🔧 The Legacy Code Modernizer

> **When to use:** You need to update old code to modern patterns without breaking things.

## Prompt Template

```
Modernize this legacy code:

[paste code]

Current: [language version, e.g., Python 2.7, ES5, Java 8]
Target: [modern version, e.g., Python 3.12, ES2024, Java 21]

Please:
1. Update to modern syntax and idioms
2. Replace deprecated APIs with current equivalents
3. Add type hints/annotations where applicable
4. Keep backward compatibility notes (if breaking changes exist)
5. List every deprecated feature you replaced and its modern equivalent
```

## Example Output

> | Old (ES5) | Modern (ES2024) | Why |
> |-----------|-----------------|-----|
> | `var` | `const`/`let` | Block scoping, prevents hoisting bugs |
> | `function(x) { return x*2 }` | `(x) => x * 2` | Concise, lexical `this` |
> | `$.ajax()` | `fetch()` + `async/await` | Native, no jQuery dependency |
> | `obj.hasOwnProperty('key')` | `Object.hasOwn(obj, 'key')` | Safer, works with `Object.create(null)` |

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
