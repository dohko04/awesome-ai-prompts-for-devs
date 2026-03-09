# ⚡ The Query Optimizer

> **When to use:** Your SQL query is slow and you need it fast.

## Prompt Template

```
Optimize this SQL query:

[paste query]

Table schemas:
[paste relevant CREATE TABLE statements or describe the schema]

Additional info:
- Database: [PostgreSQL/MySQL/SQLite/etc.]
- Table sizes: [approximate row counts]
- Current execution time: [if known]

Please:
1. Explain what the query does in plain English
2. Identify performance problems
3. Suggest indexes (with CREATE INDEX statements)
4. Rewrite the optimized query
5. Estimate the performance improvement
6. Show the EXPLAIN ANALYZE I should run to verify
```

## Example Output

> **Plain English:** "Find all orders from the last 30 days with their customer names, sorted by total amount."
>
> **Problems found:**
> 1. Missing index on `orders.created_at` — full table scan on 2M rows
> 2. `SELECT *` fetches 25 columns when you need 4
> 3. Subquery can be replaced with JOIN
>
> **Add these indexes:**
> ```sql
> CREATE INDEX idx_orders_created_at ON orders(created_at DESC);
> CREATE INDEX idx_orders_customer_id ON orders(customer_id);
> ```
>
> **Estimated improvement:** ~50x faster (from ~3s to ~60ms)

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
