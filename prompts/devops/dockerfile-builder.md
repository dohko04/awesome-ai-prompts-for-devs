# 🐳 The Dockerfile Builder

> **When to use:** You need an optimized, production-ready Docker setup.

## Prompt Template

```
Create a production-ready Dockerfile for my application:

- Language/Framework: [e.g., Node.js 20, Python 3.12, Go 1.22]
- Build command: [e.g., npm run build]
- Start command: [e.g., node dist/server.js]
- Needs: [any system dependencies, e.g., ffmpeg, chromium]
- Env vars: [list required environment variables]

Requirements:
1. Multi-stage build (keep final image small)
2. Non-root user
3. Proper .dockerignore
4. Health check
5. Layer caching optimization
6. Security best practices
7. Include docker-compose.yml for local development
```

## Example Output

> ```dockerfile
> # Build stage
> FROM node:20-alpine AS builder
> WORKDIR /app
> COPY package*.json ./
> RUN npm ci --only=production && npm cache clean --force
> COPY . .
> RUN npm run build
>
> # Production stage
> FROM node:20-alpine
> RUN addgroup -g 1001 appgroup && adduser -u 1001 -G appgroup -s /bin/sh -D appuser
> WORKDIR /app
> COPY --from=builder --chown=appuser:appgroup /app/dist ./dist
> COPY --from=builder --chown=appuser:appgroup /app/node_modules ./node_modules
> USER appuser
> EXPOSE 3000
> HEALTHCHECK --interval=30s CMD wget -q --spider http://localhost:3000/health || exit 1
> CMD ["node", "dist/server.js"]
> ```
> Final image: ~150MB (vs ~900MB without multi-stage) 🎯

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
