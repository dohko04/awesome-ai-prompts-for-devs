# ChatGPT Superapp Migration Starter

> OpenAI is merging ChatGPT, Codex, and browser into a single desktop "superapp" (March 20, 2026). Use this checklist to prepare your workflows for the transition.

## Quick Migration Checklist

```yaml
# chatgpt-superapp-readiness.yaml
# Prepare for the ChatGPT Superapp consolidation

pre_migration_checklist:
  inventory:
    - "[ ] List all OpenAI subscriptions (ChatGPT Plus, Codex, API)"
    - "[ ] Count custom GPTs and document their configs"
    - "[ ] Audit API keys — which are still active?"
    - "[ ] Calculate total monthly OpenAI spending"
  
  export_custom_gpts:
    - "[ ] For each custom GPT, save:"
    - "    - System instructions (full text)"
    - "    - Knowledge files (download copies)"
    - "    - API action schemas"
    - "    - Conversation starters"
    - "[ ] Store in version control (git repo)"
  
  document_workflows:
    - "[ ] List workflows that span multiple tools:"
    - "    - ChatGPT → Codex handoffs"
    - "    - Browse → Chat → Code loops"  
    - "    - API calls that duplicate ChatGPT features"
    - "[ ] Note pain points (context loss, re-explaining)"
  
  cost_baseline:
    chatgpt_plus: "$20/mo per seat"
    codex_pro: "$200/mo per seat"
    api_average: "$ ___/mo"
    total_current: "$ ___/mo"
    potential_savings: "Estimate 15-30% from unified context"

superapp_benefits_for_devs:
  - "Shared context: No more re-explaining your project between tools"
  - "Unified history: All chat, code, and research in one timeline"
  - "Single subscription: Likely replaces ChatGPT + Codex + browse"
  - "Workflow continuity: Research → code → test without switching apps"

what_to_do_now:
  - "Export custom GPT configs (they may become plugins)"
  - "Document cross-tool workflows for migration"
  - "Track spending for cost comparison when superapp launches"
  - "Don't build new custom GPTs — wait for superapp plugin system"
```

## Workflow Migration Template

```markdown
## Workflow: [Name]

**Current flow:**
1. Tool: ChatGPT → Action: [describe]
2. Tool: Codex → Action: [describe]  
3. Tool: Browse → Action: [describe]

**Pain points:**
- [ ] Context lost between steps
- [ ] Manual copy-paste required
- [ ] Re-explaining project context

**Superapp equivalent:**
- All steps in one unified session with shared context

**Priority to migrate:** HIGH / MEDIUM / LOW
```

---

> 💡 **Want the full pipeline?** The [AI Dev Toolkit](https://ai-dev-toolkit-five.vercel.app) includes the complete ChatGPT Superapp Developer Pipeline PRO with:
> - Automated Custom GPT exporter (Python script)
> - Unified Workflow Orchestrator with cost tracking
> - Context Sharing Architecture patterns
> - Subscription Consolidation Calculator
> - Migration timeline with beta/GA strategies
