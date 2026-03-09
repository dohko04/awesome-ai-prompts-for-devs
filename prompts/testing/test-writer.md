# ✅ The Test Writer

> **When to use:** You have code that needs tests — unit, integration, or edge cases.

## Prompt Template

```
Write comprehensive tests for this code:

[paste code]

Requirements:
- Framework: [Jest/Pytest/RSpec/etc.]
- Cover: happy path, edge cases, error cases
- Mock external dependencies
- Each test should have a clear, descriptive name that explains the scenario

Also tell me:
- What's the ideal code coverage target for this code?
- Are there any untestable parts that should be refactored?
```

## Example Output

**Input:** A `calculateDiscount(price, userType, couponCode)` function.

> ```javascript
> describe('calculateDiscount', () => {
>   // Happy path
>   it('should apply 10% discount for premium users', () => { ... });
>   it('should apply coupon discount when valid code provided', () => { ... });
>   it('should stack user discount + coupon discount', () => { ... });
>
>   // Edge cases
>   it('should return 0 discount for price of 0', () => { ... });
>   it('should cap total discount at 50%', () => { ... });
>   it('should handle floating point precision (e.g., $19.99)', () => { ... });
>
>   // Error cases
>   it('should throw for negative price', () => { ... });
>   it('should ignore expired coupon codes', () => { ... });
>   it('should treat unknown userType as regular (no discount)', () => { ... });
> });
> ```
>
> **Coverage target:** 95%+ — this is pure business logic with no I/O, so full coverage is easy and valuable.

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
