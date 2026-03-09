# 🔗 The API Integration Helper

> **When to use:** You need to integrate with a third-party API quickly and correctly.

## Prompt Template

```
I need to integrate with [API name/URL].

Here's their documentation: [paste relevant docs or link]

My stack: [language/framework]

Generate:
1. A clean service class/module that wraps the API
2. Authentication setup
3. Error handling with retries and exponential backoff
4. Rate limiting compliance
5. TypeScript types / Python models for the responses
6. Unit tests with mocked responses
7. Usage example
```

## Example Output

> ```typescript
> class StripeService {
>   private client: Stripe;
>
>   constructor(apiKey: string) {
>     this.client = new Stripe(apiKey, { apiVersion: '2024-01-01' });
>   }
>
>   async createCheckout(params: CheckoutParams): Promise<CheckoutSession> {
>     try {
>       return await this.client.checkout.sessions.create({
>         mode: 'payment',
>         line_items: params.items,
>         success_url: params.successUrl,
>         cancel_url: params.cancelUrl,
>       });
>     } catch (error) {
>       if (error instanceof Stripe.errors.StripeRateLimitError) {
>         await this.delay(1000);
>         return this.createCheckout(params); // retry once
>       }
>       throw new PaymentError('Checkout creation failed', error);
>     }
>   }
> }
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
