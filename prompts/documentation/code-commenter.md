# 💬 The Code Commenter

> **When to use:** You have complex code that needs inline documentation for your team.

## Prompt Template

```
Add clear, useful comments to this code. Follow these rules:

[paste code]

Rules:
1. DON'T comment obvious things (// increment i)
2. DO explain WHY, not WHAT
3. DO document non-obvious business logic
4. DO add JSDoc/docstring for public functions
5. DO flag potential gotchas with // ⚠️
6. Keep comments concise — one line when possible

Return the fully commented code.
```

## Example Output

> ```python
> def calculate_pricing(user, plan, billing_cycle):
>     """Calculate final price with all applicable adjustments.
>
>     Args:
>         user: User object with .created_at and .referral_code
>         plan: Plan enum (STARTER, PRO, ENTERPRISE)
>         billing_cycle: 'monthly' | 'annual'
>
>     Returns:
>         Decimal: Final price in USD (never negative)
>     """
>     base = PLAN_PRICES[plan]
>
>     # Annual billing gets 20% off — this is our main upsell lever
>     if billing_cycle == 'annual':
>         base *= Decimal('0.80')
>
>     # ⚠️ Grandfather clause: users before 2024 keep old pricing
>     if user.created_at < datetime(2024, 1, 1):
>         base = min(base, LEGACY_PRICES.get(plan, base))
>
>     return max(base, Decimal('0'))  # Guard against negative prices
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
