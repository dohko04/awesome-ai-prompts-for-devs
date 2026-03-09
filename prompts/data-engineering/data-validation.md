# ✔️ The Data Validation Prompt

> **When to use:** You need to validate data quality, find anomalies, or build data checks.

## Prompt Template

```
Create data validation checks for this dataset/table:

Schema: [describe columns, types, and what the data represents]
Business rules: [e.g., "price must be > 0", "email must be unique"]

Generate:
1. SQL queries to check each business rule
2. Anomaly detection queries (outliers, suspicious patterns)
3. Completeness checks (null rates per column)
4. Consistency checks (cross-table relationships)
5. A summary query that returns a "data health score"
6. Suggested automated monitoring (great-expectations/dbt tests)
```

## Example Output

> ```sql
> -- Data Health Dashboard
> SELECT
>   COUNT(*) as total_rows,
>   COUNT(*) FILTER (WHERE email IS NULL) as missing_emails,
>   COUNT(*) FILTER (WHERE price <= 0) as invalid_prices,
>   COUNT(*) - COUNT(DISTINCT email) as duplicate_emails,
>   ROUND(100.0 * COUNT(*) FILTER (WHERE price > 0 AND email IS NOT NULL)
>     / COUNT(*), 1) as health_score_pct
> FROM orders;
> ```
> Health score: 98.5% → ✅ Healthy | <95% → ⚠️ Investigate | <90% → 🔴 Alert

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
