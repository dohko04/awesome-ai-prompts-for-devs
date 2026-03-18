# Manus "My Computer" Desktop AI Agent Setup

> Free starter guide for configuring and using Manus's local desktop AI agent for file and application automation on macOS/Windows.

## What This Solves
Manus "My Computer" turns your desktop into an AI-controlled workspace — reading, editing, and acting on local files and applications without cloud dependency. This guide helps you set up effective workflows and safety boundaries.

## Quick Setup

### 1. Define Your Agent Boundaries
```yaml
# manus-config.yaml
agent:
  name: "desktop-assistant"
  mode: "supervised"  # supervised | autonomous
  
permissions:
  file_system:
    read: ["~/Projects", "~/Documents"]
    write: ["~/Projects"]
    deny: ["~/.ssh", "~/.aws", "~/.*credentials*"]
  
  applications:
    allow: ["Terminal", "VS Code", "Chrome", "Finder"]
    deny: ["System Preferences", "Keychain Access"]
  
  network:
    allow_outbound: true
    deny_domains: ["*.internal.company.com"]
```

### 2. Create Task Templates
```yaml
# tasks/code-review.yaml
task: "code-review"
description: "Review recent changes in a project"
steps:
  - open_app: "Terminal"
  - run: "cd {{project_path}} && git diff --stat HEAD~5"
  - analyze: "Summarize changes and flag potential issues"
  - open_app: "VS Code"
  - action: "Open files with issues for detailed review"

# tasks/daily-standup-prep.yaml
task: "standup-prep"
description: "Prepare daily standup summary"
steps:
  - run: "cd {{project_path}} && git log --oneline --since='yesterday'"
  - read_file: "{{project_path}}/TODO.md"
  - generate: "Create standup summary: done, doing, blockers"
  - write_file: "~/Documents/standups/{{date}}.md"
```

### 3. Safety Checklist
```markdown
Before enabling autonomous mode:
- [ ] Restricted sensitive directories (~/.ssh, credentials)
- [ ] Limited application access to necessary apps only
- [ ] Enabled session logging for audit trail
- [ ] Set maximum actions per session (recommended: 50)
- [ ] Tested in supervised mode for at least 1 week
```

## Key Tips
- Always start in `supervised` mode — review every action before approving
- Create explicit deny lists for sensitive paths BEFORE enabling automation
- Use task templates to constrain agent behavior to known workflows
- Log every session for audit and debugging

## Limitations of This Free Version
- Single-task templates only
- No multi-agent desktop coordination
- Basic permission model (no role-based access)
- No integration with CI/CD or team workflows

---

🔥 **Want the full production pipeline?** The [AI Dev Toolkit PRO](https://ai-dev-toolkit-five.vercel.app) includes multi-agent desktop orchestration, enterprise permission models with RBAC, CI/CD integration for automated desktop workflows, team rollout playbooks, cost tracking, and security hardening guides.
