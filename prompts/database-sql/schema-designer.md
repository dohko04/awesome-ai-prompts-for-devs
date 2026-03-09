# 📐 The Schema Designer

> **When to use:** You're designing a database from scratch or adding major features.

## Prompt Template

```
Design a database schema for: [describe the domain]

Requirements:
- [list key entities and relationships]
- Database: [PostgreSQL/MySQL/MongoDB/etc.]
- Scale: [expected data volume]

Provide:
1. Entity-Relationship overview (ASCII or text)
2. CREATE TABLE statements with appropriate types
3. Indexes for common query patterns
4. Constraints (unique, check, foreign keys)
5. Explain any denormalization decisions
6. Migration strategy if this extends an existing schema
```

## Example Output

> ```sql
> CREATE TABLE organizations (
>     id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
>     name VARCHAR(255) NOT NULL,
>     plan plan_type NOT NULL DEFAULT 'free',
>     created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
> );
>
> CREATE TABLE subscriptions (
>     id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
>     org_id UUID NOT NULL REFERENCES organizations(id),
>     plan plan_type NOT NULL,
>     status subscription_status NOT NULL DEFAULT 'active',
>     current_period_end TIMESTAMPTZ NOT NULL,
>     -- Denormalized: avoids JOIN on every auth check
>     seats_used INT NOT NULL DEFAULT 0,
>     seats_limit INT NOT NULL DEFAULT 5
> );
>
> CREATE INDEX idx_sub_org_status ON subscriptions(org_id, status);
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
