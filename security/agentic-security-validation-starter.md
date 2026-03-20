# Agentic Security Validation Starter

> AI agents that autonomously test and detect security vulnerabilities in your codebase.
> Trending: March 16-20, 2026 — Agentic security validation is the hottest AppSec topic.

## Basic Security Validation Agent

```python
#!/usr/bin/env python3
"""basic_security_agent.py — Scans code for common vulnerabilities."""

import re
import os

RULES = [
    (r'eval\(', "Arbitrary code execution (eval)", "CWE-95", "HIGH"),
    (r'exec\(', "Arbitrary code execution (exec)", "CWE-95", "HIGH"),
    (r'subprocess.*shell\s*=\s*True', "Shell injection risk", "CWE-78", "HIGH"),
    (r'pickle\.loads', "Insecure deserialization", "CWE-502", "HIGH"),
    (r'verify\s*=\s*False', "TLS verification disabled", "CWE-295", "MEDIUM"),
    (r'DEBUG\s*=\s*True', "Debug mode in production", "CWE-489", "MEDIUM"),
    (r'password\s*=\s*["\'][^"\']+["\']', "Hardcoded password", "CWE-798", "CRITICAL"),
]

def scan_file(filepath: str) -> list[dict]:
    findings = []
    with open(filepath) as f:
        for line_num, line in enumerate(f, 1):
            for pattern, title, cwe, severity in RULES:
                if re.search(pattern, line):
                    findings.append({
                        "file": filepath,
                        "line": line_num,
                        "title": title,
                        "cwe": cwe,
                        "severity": severity,
                    })
    return findings

def scan_directory(path: str) -> list[dict]:
    all_findings = []
    for root, _, files in os.walk(path):
        for f in files:
            if f.endswith(('.py', '.js', '.ts')):
                all_findings.extend(scan_file(os.path.join(root, f)))
    return all_findings

if __name__ == "__main__":
    import sys
    findings = scan_directory(sys.argv[1] if len(sys.argv) > 1 else ".")
    for f in findings:
        print(f"[{f['severity']}] {f['file']}:{f['line']} — {f['title']} ({f['cwe']})")
    print(f"\nTotal: {len(findings)} findings")
```

## Quick CI Integration

```yaml
# Add to your GitHub Actions workflow
- name: Security Scan
  run: |
    pip install bandit semgrep
    bandit -r src/ --severity-level medium || true
    semgrep --config=auto src/ || true
```

---

**Want the full pipeline?** The PRO version includes:
- Multi-agent security orchestrator (SAST + secrets + deps + config)
- CI/CD pipeline with security scoring and PR comments
- Auto-remediation agent (fixes common vulns automatically)
- Grafana security posture dashboard
- Agentic penetration testing playbook

👉 **[AI Dev Toolkit — 266 Pro Resources, $9 USD](https://ai-dev-toolkit-five.vercel.app)**
