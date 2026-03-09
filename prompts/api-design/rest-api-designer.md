# 🛠️ The REST API Designer

> **When to use:** You need to design a clean, well-documented REST API from scratch.

## Prompt Template

```
Design a REST API for: [feature/resource]

Context:
- What it does: [describe the feature]
- Who consumes it: [frontend app, mobile, third-party]
- Authentication: [JWT/API Key/OAuth]
- Expected load: [requests per minute]

Provide:
1. Endpoint list (method, path, description)
2. Request/response schemas (JSON with types)
3. Error response format (consistent across all endpoints)
4. Pagination strategy (cursor vs offset)
5. Rate limiting headers
6. Versioning strategy
7. OpenAPI/Swagger snippet for the main endpoint
```

## Example Output

> | Method | Path | Description |
> |--------|------|-------------|
> | GET | `/api/v1/products` | List products (paginated) |
> | POST | `/api/v1/products` | Create product |
> | PATCH | `/api/v1/products/:id` | Update product |
> | DELETE | `/api/v1/products/:id` | Soft-delete product |
>
> **Error format (all endpoints):**
> ```json
> {
>   "error": {
>     "code": "PRODUCT_NOT_FOUND",
>     "message": "Product with ID 'abc' does not exist",
>     "requestId": "req_abc123"
>   }
> }
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
