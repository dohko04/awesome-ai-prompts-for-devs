# Apple App Store Vibe Code Compliance Checker

> As of March 18 2026, Apple is blocking vibe coding apps (Replit, Vibecode) from updating on the App Store, citing Guideline 2.5.2 (no dynamic code execution). Use this prompt to audit your vibe-coded app before submission.

## The Prompt

```
You are an iOS App Store compliance specialist focused on vibe-coded applications.

I'm building an app using [VIBE_CODING_TOOL: e.g., Replit, Vibecode, Cursor, Bolt.new].

Audit my app for App Store Guideline 2.5.2 compliance:

1. **Dynamic Code Detection**: Identify any code that dynamically generates, downloads, or executes other code at runtime
2. **WebView Audit**: Flag any WebView usage that could be interpreted as running a "sub-app"
3. **Sandbox Boundaries**: Check if the app stays within its own sandbox or reaches into other app domains
4. **Review Checklist**: Generate a pre-submission checklist specific to vibe-coded apps

For each violation found, provide:
- The specific guideline being violated
- The offending code pattern
- A compliant alternative that preserves the feature

App description: [DESCRIBE_YOUR_APP]
Tech stack: [YOUR_STACK]
```

## What You Get (Free)
- Basic compliance audit for Guideline 2.5.2
- Common violation patterns for vibe-coded apps

## What the PRO Version Adds
The full **Apple Vibe Code Compliance Pipeline** ($9 in the AI Dev Toolkit) includes:
- 🔍 Automated scanner script that crawls your codebase for 15+ violation patterns
- 📋 Full Apple Guidelines cross-reference (2.5.2, 4.2, 4.7) with vibe-coding edge cases
- 🔄 Pre-submission CI/CD gate that blocks deploys with compliance issues
- 📊 Rejection appeal template generator (based on real successful appeals)
- 🏗️ Architecture patterns for compliant vibe-coded apps (hybrid native + web approach)

👉 **Get the full toolkit**: https://ai-dev-toolkit-five.vercel.app
