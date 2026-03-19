# AI Dev Tool Infostealer Defense — Verification Checklist

> Protect yourself from fake AI developer tool downloads. Verify before you install — attackers are now impersonating Claude Code, OpenClaw, and other popular AI coding tools.

**Trending:** Kaspersky discovered (March 18, 2026) a campaign using sponsored search ads to distribute Amatera infostealer via fake Claude Code and OpenClaw download pages. Targets: developers on Windows/macOS searching for AI tool installation instructions.

## The Prompt

```
You are a security-focused developer assistant. Help me verify that an AI developer tool I'm about to install is legitimate and not malware disguised as a popular tool.

## Tool I Want to Install
Name: [TOOL_NAME]
Source URL: [WHERE_I_FOUND_IT]
Installation method: [npm/pip/curl/brew/binary download/other]

## Verification Checklist

### 1. Source Verification
- [ ] URL matches the OFFICIAL domain (not a lookalike)
  - Claude Code → anthropic.com or npmjs.com/package/@anthropic-ai/claude-code
  - OpenClaw → github.com/openclaw (verify org)
  - Cursor → cursor.com (not cursor-ai.com, cursorai.com, etc.)
- [ ] NOT from a sponsored search ad (attackers buy ads for "X download")
- [ ] NOT from a Squarespace/Wix/random landing page

### 2. Package Verification
- [ ] Check npm/PyPI publisher matches official org
- [ ] Verify package creation date (new packages mimicking old tools = red flag)
- [ ] Check download count (legitimate tools have thousands+ weekly downloads)
- [ ] Compare SHA256 hash with official release notes

### 3. Installation Command Audit
- [ ] Command doesn't pipe curl to bash from unknown URLs
- [ ] No hidden redirects (curl -L to different domain)
- [ ] No PowerShell encoded commands
- [ ] No requests for unnecessary permissions (admin/root for a code editor?)

### 4. Post-Install Verification
- [ ] Check what processes started (ps aux | grep [tool])
- [ ] Check network connections (netstat -an | grep ESTABLISHED)
- [ ] Verify no new browser extensions were installed
- [ ] Check for new files in ~/Library, AppData, or ~/.config

## Red Flags Summary
Output a risk score (LOW/MEDIUM/HIGH/CRITICAL) based on findings.
```

## Known Attack Patterns (March 2026)

| Attack Vector | Target Tool | Malware | What It Steals |
|---|---|---|---|
| Sponsored search ads | Claude Code | Amatera | Browser data, crypto wallets, user files |
| Fake GitHub repos | OpenClaw | Amatera | Same as above |
| Typosquatted npm packages | Various AI tools | Credential harvesters | .env files, API keys, SSH keys |

## Quick Defense Rules

1. **NEVER click sponsored ads** for developer tool downloads
2. **Always go to the official GitHub/website** directly
3. **Use package managers** (npm, pip, brew) not binary downloads
4. **Check the URL letter by letter** before running install commands
5. **Use a sandbox** (Docker, VM) for first-time installs of new tools

---

> 💡 **Want the full production version?** The PRO resource includes: automated download source verifier (Python script), CI/CD supply chain security gates, real-time threat intelligence integration, team security policy generator, and incident response playbook for compromised dev machines.
>
> **Get it at:** [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) — 220+ production-ready resources for $9 USD.
