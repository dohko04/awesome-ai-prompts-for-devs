# AI Dev Tool Supply Chain Security Audit

> Verify that your AI development tools (Claude Code, Cursor, Copilot, etc.) are genuine and not infostealers. Based on real threats discovered in March 2026.

## Why This Matters

Kaspersky discovered active campaigns distributing infostealers disguised as popular AI dev tools. Attackers create fake installation guides and packages that look identical to real ones but steal credentials, API keys, and SSH keys.

## The Prompt

```
You are an AI development environment security auditor. I need you to help me audit my AI tool installations for supply chain attacks.

## Context
In March 2026, security researchers found infostealers mimicking popular AI dev tools (Claude Code, Cursor, Copilot plugins, MCP servers). Attackers use:
- Fake npm/pip packages with typosquatted names
- Modified installation scripts from SEO-poisoned "how to install" guides
- Malicious VS Code extensions impersonating official ones
- Tampered MCP server configs that exfiltrate context to attacker endpoints

## My Environment
- OS: [YOUR_OS]
- AI Tools installed: [LIST_YOUR_TOOLS]
- Package managers: [npm/pip/brew/etc.]

## Audit Checklist — Run These Now

### 1. Verify Package Authenticity
For each AI tool, confirm:
- Installed from official source (not a blog/tutorial link)
- Package name matches exactly (no typosquats like `claude-cod` or `curssor`)
- Check signatures: `npm audit signatures` / `pip hash`

### 2. Check for Suspicious Outbound Connections
```bash
# macOS/Linux - check what your AI tools are connecting to
lsof -i -P | grep -i "cursor\|claude\|copilot\|cline"
# Or use: ss -tunap | grep -E "cursor|claude|copilot"
```

### 3. Audit MCP Server Configs
Review every MCP config for:
- Unknown server URLs (should only be localhost or official endpoints)
- Unexpected `env` variables being passed (credential harvesting)
- Servers you didn't install

```bash
# Find all MCP configs
find ~ -name "*.mcp.json" -o -name "mcp_config.json" 2>/dev/null
# Review each one manually
```

### 4. VS Code Extension Verification
```bash
# List all AI-related extensions
code --list-extensions | grep -iE "claude|copilot|cursor|cline|continue|aider"
# For each: verify publisher matches official (e.g., "GitHub.copilot" not "GitHubb.copilot")
```

### 5. Environment Variable Audit
```bash
# Check for unexpected API key env vars being set
env | grep -iE "api.key|token|secret|openai|anthropic|claude"
# Review shell profiles for suspicious exports
grep -r "export.*KEY\|export.*TOKEN\|export.*SECRET" ~/.bashrc ~/.zshrc ~/.profile 2>/dev/null
```

## Output Format
For each finding, report:
- **Tool**: name and version
- **Status**: ✅ Verified / ⚠️ Suspicious / 🔴 Compromised
- **Evidence**: what you checked and found
- **Action**: what to do if suspicious

Flag anything that:
- Connects to non-official domains
- Has mismatched package names/publishers
- Exports credentials to unexpected locations
- Was installed from unofficial sources
```

## Quick Wins

1. **Always install from official docs** — never from random blog posts
2. **Pin versions** in your package.json / requirements.txt
3. **Audit MCP configs weekly** — they have full context access
4. **Use `npm audit signatures`** before installing AI packages
5. **Monitor outbound connections** with `lsof` or Little Snitch

## Example Output

```
## AI Tool Supply Chain Audit Report — 2026-03-11

| Tool | Version | Source | Status | Notes |
|------|---------|--------|--------|-------|
| Claude Code | 1.2.3 | npm (official) | ✅ Verified | Signature matches |
| Cursor | 0.48.1 | cursor.com | ✅ Verified | Direct download |
| cline | 3.1.0 | VS Code Marketplace | ⚠️ Check | Publisher name differs from expected |
| mcp-server-github | 1.0.5 | npm | 🔴 Alert | Typosquatted package — should be @modelcontextprotocol/server-github |

### Immediate Actions:
1. Uninstall `mcp-server-github` — replace with official `@modelcontextprotocol/server-github`
2. Rotate all API keys that were in environment during exposure
3. Check git history for unauthorized commits
```

---

> 🔒 **Want the full Security Pipeline?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes automated scanning scripts, CI/CD security gates, and a complete MCP server allowlist manager. One compromised tool can leak your entire codebase.
