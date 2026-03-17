# 1Password AI Agent Credential Security — Starter

> Secure your AI coding agents (Cursor, Copilot, Claude Code) with zero-trust credential management. Based on 1Password's March 17, 2026 Unified Access Platform launch.

## The Problem

AI agents need API keys, database URLs, and cloud credentials. If you're using `.env` files or hardcoded secrets — you're one git push away from a breach.

## Quick Setup: Secret References (Never Embed)

```bash
# Install 1Password CLI
brew install 1password-cli  # macOS
# or: sudo apt install 1password-cli  # Linux

# Sign in
op signin

# Store your AI keys
op item create --category=api-credential --title="OpenAI Key" \
  --vault="Development" credential="sk-your-key-here"

op item create --category=api-credential --title="Anthropic Key" \
  --vault="Development" credential="sk-ant-your-key-here"
```

## Use References Instead of Values

```bash
# ❌ NEVER
export OPENAI_API_KEY="sk-actual-key-here"

# ✅ ALWAYS: Reference that resolves at runtime
export OPENAI_API_KEY=$(op read "op://Development/OpenAI Key/credential")
```

## Pre-Commit Secret Scanner

```bash
#!/bin/bash
# Save as .git/hooks/pre-commit && chmod +x
PATTERNS='sk-[a-zA-Z0-9]{20,}|sk-ant-[a-zA-Z0-9]{20,}|ghp_[a-zA-Z0-9]{36}|AKIA[A-Z0-9]{16}'
if git diff --cached | grep -qP "$PATTERNS"; then
  echo "🚨 BLOCKED: Potential secret detected in commit!"
  echo "Use 1Password references: op://Vault/Item/Field"
  exit 1
fi
```

## Cursor Integration

```json
// .cursor/settings.json
{
  "ai.secretProvider": "1password",
  "ai.secretVault": "Development"
}
```

---

🔒 **Want the full pipeline?** The PRO version includes:
- Multi-agent credential architecture (YAML policies per agent type)
- CI/CD integration (GitHub Actions + Docker with 1Password)
- Automated credential rotation system
- Compliance dashboard & audit reporting
- Team rollout playbook

→ **[Get the full AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app)** — 190+ production-ready resources for $9
