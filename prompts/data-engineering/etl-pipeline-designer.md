# 🔀 The ETL Pipeline Designer

> **When to use:** You need to extract, transform, and load data between systems.

## Prompt Template

```
Design an ETL pipeline:

Source: [database/API/file format — describe the data]
Destination: [data warehouse/database/file]
Frequency: [real-time / hourly / daily]
Volume: [rows per run, total data size]
Transformations needed: [list data transformations]

Provide:
1. Pipeline architecture (source → stages → sink)
2. Code for each stage (Python/SQL/your preferred language)
3. Error handling (what happens when source is down? duplicate data?)
4. Idempotency strategy (safe to re-run without duplicates)
5. Monitoring and alerting
6. Backfill strategy for historical data
```

## Example Output

> **Architecture:**
> ```
> [Postgres] → Extract (CDC) → [Kafka] → Transform (dbt) → [BigQuery] → [Dashboard]
> ```
>
> **Idempotency:** Use `MERGE`/`UPSERT` with natural keys:
> ```sql
> MERGE INTO analytics.orders AS target
> USING staging.orders AS source
> ON target.order_id = source.order_id
> WHEN MATCHED THEN UPDATE SET ...
> WHEN NOT MATCHED THEN INSERT ...
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
