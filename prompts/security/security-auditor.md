# 🛡️ The Security Auditor

> **When to use:** You want to find security vulnerabilities in your code before attackers do.

## Prompt Template

```
Perform a security audit on this code:

[paste code]

Context:
- This code handles: [auth/payments/user data/file uploads/etc.]
- Exposed to: [public internet / internal only / admin only]
- Framework: [Express/Django/Rails/etc.]

Check for:
1. Injection vulnerabilities (SQL, XSS, command injection)
2. Authentication/authorization flaws
3. Data exposure (logs, error messages, API responses)
4. Cryptography issues (weak hashing, hardcoded secrets)
5. Dependency vulnerabilities
6. OWASP Top 10 compliance

For each finding:
- Severity: Critical / High / Medium / Low
- CWE reference
- Exploit scenario (how an attacker would use this)
- Fix with code example
```

## Example Output

> **🔴 Critical — Stored XSS (CWE-79)**
> ```javascript
> // ❌ Current: user input rendered as HTML
> element.innerHTML = userComment;
>
> // ✅ Fix: use textContent or sanitize
> element.textContent = userComment;
> // OR: DOMPurify.sanitize(userComment)
> ```
> **Exploit:** Attacker submits `<script>...</script>` as a comment. Every user who views the page sends their session cookie to the attacker.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
