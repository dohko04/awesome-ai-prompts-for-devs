# AI Code Runtime Risk Checker (FREE)

> Quick checklist to detect non-deterministic failures in AI-generated code before they hit production.

## The Problem

AI-generated code passes tests but fails unpredictably in production. Traditional testing can't catch **emergent** runtime failures.

## Quick Risk Checklist

```yaml
# Run this checklist on every PR with AI-generated code

runtime_risk_check:
  non_determinism:
    - "Does the code produce consistent output for the same input?"
    - "Are there hidden random/time-dependent behaviors?"
    - "Could concurrent requests cause race conditions?"
  
  edge_cases:
    - "Does it handle null/undefined/empty inputs?"
    - "What happens at 10x normal traffic?"
    - "Are all API calls properly timeout-wrapped?"
  
  observability:
    - "Can you trace a request through AI-generated code?"
    - "Are errors logged with enough context to debug?"
    - "Do you have metrics on this code path?"
  
  ai_specific:
    - "Did the AI hallucinate any API methods?"
    - "Is error handling consistent with the rest of the codebase?"
    - "Are there O(n²) patterns hidden in simple-looking code?"
```

## Quick Detection Script

```bash
# Check for common AI code risks in changed files
git diff --name-only origin/main | while read f; do
  echo "--- $f ---"
  # Missing error handling
  FUNCS=$(grep -c 'function\|def \|async ' "$f" 2>/dev/null || echo 0)
  CATCHES=$(grep -c 'catch\|except\|rescue' "$f" 2>/dev/null || echo 0)
  echo "  Functions: $FUNCS, Error handlers: $CATCHES"
  
  # Hallucinated APIs (methods not in package.json/requirements.txt)
  # Generic variable names (AI signature)
  GENERIC=$(grep -c '\b\(temp\|result\|data\|output\|response\)\b' "$f" 2>/dev/null || echo 0)
  echo "  Generic variable names: $GENERIC"
done
```

## Red Flags to Watch For

| Signal | Risk | Action |
|--------|------|--------|
| Same input, different output | Critical | Add deterministic wrappers |
| No error handling on new code | High | Add try/catch + logging |
| Generic variable names everywhere | Medium | Rename for clarity |
| API methods not in docs | Critical | Verify every external call |
| Latency spikes after deploy | High | Add observability, canary deploy |

---

### 🔥 Want the Full Pipeline?

The **AI Code Runtime Risk Observer PRO** includes:
- Automated AI code fingerprint scanner (YAML config)
- Python runtime anomaly detector with non-determinism detection
- CI/CD risk gate (GitHub Actions)
- Grafana dashboard config
- Cost & risk calculator

**Get it in the [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 196+ production-ready resources for $9.**
