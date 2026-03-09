# 🔄 The CI/CD Pipeline Designer

> **When to use:** You need to set up or improve your CI/CD pipeline.

## Prompt Template

```
Design a CI/CD pipeline for my project:

- Repository: [GitHub/GitLab/Bitbucket]
- Language: [e.g., TypeScript, Python]
- Deployment target: [Vercel/AWS/GCP/Railway/etc.]
- Branch strategy: [main only / main + develop / gitflow]
- Requirements: [linting, tests, type checking, etc.]

Generate:
1. Complete workflow file (.github/workflows/ or .gitlab-ci.yml)
2. Stages: lint → test → build → deploy
3. Caching strategy for fast builds
4. Environment-specific deployments (staging/production)
5. Slack/Discord notifications on failure
6. Security scanning step
```

## Example Output

> ```yaml
> name: CI/CD
> on:
>   push:
>     branches: [main, develop]
>   pull_request:
>     branches: [main]
>
> jobs:
>   quality:
>     runs-on: ubuntu-latest
>     steps:
>       - uses: actions/checkout@v4
>       - uses: actions/setup-node@v4
>         with: { node-version: 20, cache: 'npm' }
>       - run: npm ci
>       - run: npm run lint
>       - run: npm run typecheck
>       - run: npm test -- --coverage
>
>   deploy:
>     needs: quality
>     if: github.ref == 'refs/heads/main'
>     # ...deployment steps
> ```

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
