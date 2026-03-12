# 🛡️ AI Code Output Validator

> **When to use:** Before merging ANY AI-generated code. Catches hallucinations, deprecated APIs, security holes, and logic errors that AI coding tools commonly introduce.

## Why This Exists

AI coding tools (Copilot, Cursor, Claude Code, Kiro) generate plausible-looking code that often:
- References APIs that don't exist (hallucinated imports)
- Uses deprecated patterns from training data
- Introduces subtle security vulnerabilities
- Breaks existing functionality it wasn't told about
- Creates "working" code with hidden performance issues

This validator catches those problems BEFORE they reach production.

## Prompt Template

```markdown
You are a code validator specializing in AI-generated code review.

Review this AI-generated code for the following categories:

CODE:
[paste AI-generated code here]

LANGUAGE/FRAMEWORK: [e.g., Python 3.12, React 19, Swift 6]

## Validation Checklist

### 1. Hallucination Check
- Do ALL imported modules/packages actually exist?
- Are ALL function/method names real for the specified version?
- Do the API signatures match the actual library docs?
- Flag any function that "looks right" but doesn't exist

### 2. Version Compatibility
- Is this code valid for the specified language version?
- Any deprecated APIs being used?
- Any syntax from future/past versions?

### 3. Security Scan
- SQL injection vectors
- Unsanitized user input
- Hardcoded secrets/credentials
- Insecure defaults (HTTP instead of HTTPS, weak crypto)
- Path traversal vulnerabilities

### 4. Logic Verification
- Off-by-one errors
- Null/undefined handling gaps
- Race conditions in async code
- Error handling completeness (happy path only?)

### 5. Integration Risk
- Would this break existing code if dropped in?
- Missing imports or dependencies?
- Conflicting function/variable names?

For each issue found:
- 🔴 BLOCK — Must fix before merge
- 🟡 WARN — Should fix, may cause problems
- 🔵 NOTE — Style/improvement suggestion

Output format:
VERDICT: ✅ SAFE / ⚠️ NEEDS FIXES / 🚫 REJECT
Issues: [list]
Fixed code: [if applicable]
```

## Example

Input (AI-generated Python):
```python
from fastapi import FastAPI
from pydantic import validator  # ← deprecated in Pydantic v2

app = FastAPI()

@app.get("/users/{user_id}")
async def get_user(user_id: str):
    query = f"SELECT * FROM users WHERE id = '{user_id}'"  # ← SQL injection!
    return await db.execute(query)
```

Output:
```
VERDICT: 🚫 REJECT

🔴 BLOCK — SQL Injection (line 7)
  f-string in SQL query allows injection.
  Fix: Use parameterized query: db.execute("SELECT * FROM users WHERE id = $1", user_id)

🟡 WARN — Deprecated import (line 2)  
  `from pydantic import validator` → use `field_validator` in Pydantic v2
  Fix: from pydantic import field_validator

🔵 NOTE — Missing input validation
  user_id should validate format (UUID?) before query
```

## Limitations

This free version covers single-file validation. For production teams you need:
- Multi-file dependency graph analysis
- CI/CD integration (auto-validate every AI-generated PR)
- Custom rule engine for your team's patterns
- Historical tracking of AI error rates per tool
- Auto-fix pipeline with before/after diffs

---

> 🔥 **Want the complete AI Code Validation Pipeline?** CI/CD integration + custom rules + auto-fix → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
