# Skylos AI Code Security Analyzer Starter (FREE)

> Use Skylos (static analysis + local LLM agents) to find vulnerabilities, dead code, and security issues in your codebase — all running locally, no data leaves your machine. Based on the Skylos launch (GitHub trending, March 2026).

## Why This Matters

AI coding agents write code fast, but they also introduce non-obvious vulnerabilities: unused imports that pull in compromised packages, dead code paths that bypass auth, and subtle logic flaws that only show up in production. Skylos combines static analysis with a local LLM agent to catch what linters miss.

## Quick Start

```bash
# Install Skylos
pip install skylos

# Run full analysis on your project
skylos analyze ./src --output report.json

# Run with local LLM agent for deeper analysis
skylos analyze ./src --agent --model ollama/codellama:13b
```

## Security Scan Workflow

```yaml
# skylos-scan.yaml — What to scan and when

scan_triggers:
  pre_commit:
    - "New dependencies added (supply chain risk)"
    - "Auth/permission code modified"
    - "API endpoint handlers changed"
  
  pr_review:
    - "Full codebase scan"
    - "Dead code detection"
    - "Dependency vulnerability check"
  
  weekly:
    - "Deep LLM-powered code review"
    - "Attack surface mapping"
    - "Compliance drift detection"

scan_categories:
  critical:
    - "SQL injection patterns"
    - "Hardcoded secrets/credentials"
    - "Broken authentication flows"
    - "Unvalidated file uploads"
  
  high:
    - "Unused dependencies (supply chain bloat)"
    - "Dead code paths (hidden attack surface)"
    - "Missing input validation"
    - "Insecure deserialization"
  
  medium:
    - "Overly permissive CORS"
    - "Missing rate limiting"
    - "Verbose error messages (info leakage)"
    - "Deprecated API usage"
```

## AI Agent Enhancement Prompt

```markdown
You are a security-focused code reviewer using Skylos static analysis results.

Given the Skylos report below, provide:
1. **Critical findings** — must fix before deploy (with exact file:line)
2. **Supply chain risks** — unused/suspicious dependencies
3. **Dead code audit** — code paths that could hide vulnerabilities
4. **Remediation plan** — prioritized fixes with estimated effort

Rules:
- Flag any AI-generated code patterns (repetitive, boilerplate-heavy)
- Check for "hallucinated" imports (packages that don't exist → typosquatting risk)
- Verify all auth middleware is applied consistently
- Look for test files accidentally included in production builds
```

## CI/CD Integration

```yaml
# .github/workflows/skylos-security.yml
name: Skylos Security Scan
on: [pull_request]

jobs:
  security-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: pip install skylos
      - run: skylos analyze ./src --format sarif --output skylos.sarif
      - uses: github/codeql-action/upload-sarif@v3
        with:
          sarif_file: skylos.sarif
```

---

> 🔒 **Want the full security pipeline?** The PRO version includes: automated red team agent, LLM-powered remediation engine, compliance mapping (SOC2/HIPAA/GDPR), dependency graph attack surface visualizer, and Grafana security dashboard.
>
> **Get the complete AI Dev Toolkit** → [ai-dev-toolkit](https://ai-dev-toolkit-five.vercel.app)
