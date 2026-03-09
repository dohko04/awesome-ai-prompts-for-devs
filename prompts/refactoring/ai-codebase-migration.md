# 🔄 AI-Assisted Codebase Migration

> Use AI to plan and execute large-scale codebase migrations — framework upgrades, language ports, monolith-to-microservices, and more.

## The Prompt

```
You are a senior migration architect. Help me plan and execute a codebase migration using AI tools.

**Migration type:** [choose one]
- Framework upgrade (e.g., React class → hooks, Next.js Pages → App Router)
- Language port (e.g., JavaScript → TypeScript, Python 2 → 3)
- Architecture change (e.g., monolith → microservices, REST → GraphQL)
- Library swap (e.g., Moment.js → date-fns, Express → Fastify)

**Codebase details:**
- Size: [e.g., ~200 files, 50K lines]
- Language/framework: [current stack]
- Target: [what you're migrating to]
- Test coverage: [percentage if known]

Generate:

1. **Migration analysis** (run this first):
   - Script to scan codebase and categorize files by migration complexity
   - Dependency graph of what needs to migrate in which order
   - Risk assessment: which files are hardest to migrate and why
   - Estimated effort per file category

2. **AI migration prompts** (one per file category):
   - Specific prompt template optimized for each type of change
   - Include "before" pattern matching and "after" expected output
   - Chain-of-thought instructions so AI explains each transformation
   - Validation checklist for human review

3. **Batch migration script**:
   - Process files in dependency order
   - Use AI API to transform each file
   - Run existing tests after each file migration
   - Generate diff for human review before committing
   - Track progress in a migration dashboard (markdown table)

4. **Rollback strategy**:
   - Feature flags for gradual rollout
   - Git branch strategy for parallel old/new code
   - Automated smoke tests comparing old vs new behavior

5. **Migration tracking document**:
   - Progress dashboard template
   - Decision log for edge cases
   - Known issues and workarounds

Output the analysis script and batch migration script as runnable code.
Format prompts as copy-paste ready templates.
```

## Example Output

- `scripts/analyze-migration.ts` — codebase scanner
- `scripts/batch-migrate.ts` — AI-powered batch transformer
- `prompts/migrate-*.md` — per-category migration prompts
- `MIGRATION.md` — tracking dashboard
- `migration-config.json` — settings and rules

## Why This Matters (March 2026)

The TypeScript surge (66% growth, now GitHub's #1 language) means millions of JS files need migration. AI tools can handle **70-80% of mechanical transformations** — but only with the right prompts and validation. This workflow turns a months-long project into weeks.

## Pro Tips

- Always migrate tests FIRST — they become your safety net for everything else
- Run the analysis script before committing to a timeline
- Use the batch script on a branch and review diffs before merging
- The "comparison smoke test" catches subtle behavioral changes AI might introduce

---

> 💡 **Want the complete version?** The [Full AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes migration prompt chains for 10 common scenarios (React, Next.js, Express, Django, etc.), a visual progress dashboard, and cost estimation templates.
