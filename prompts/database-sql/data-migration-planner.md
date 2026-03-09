# 🚚 The Data Migration Planner

> **When to use:** You need to migrate data between schemas, databases, or formats safely.

## Prompt Template

```
I need to migrate data:

FROM: [current schema/structure/database]
TO: [target schema/structure/database]

Constraints:
- Downtime tolerance: [zero/minutes/hours]
- Data volume: [approximate size]
- Must preserve: [any specific data integrity rules]

Create a migration plan with:
1. Pre-migration checklist (backups, validation)
2. Step-by-step migration script
3. Rollback plan if something goes wrong
4. Data validation queries (before vs. after counts, checksums)
5. Estimated duration
```

## Example Output

> **Pre-migration checklist:**
> - [ ] Backup: `pg_dump -Fc mydb > pre_migration_backup.dump`
> - [ ] Verify row counts: `SELECT COUNT(*) FROM users; -- expect 145,832`
> - [ ] Notify team, set maintenance window
>
> **Rollback:** `pg_restore -d mydb pre_migration_backup.dump` (estimated: 3 min for this data size)

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
