# Gemini Chrome Dev Workflow Builder

> Build a personalized developer workflow using Gemini's built-in Chrome sidebar for research, debugging, and code review — without leaving your browser.

## The Prompt

```
You are a senior developer workflow architect. I need you to design a complete
browser-based development workflow using Gemini's built-in Chrome sidebar.

My context:
- Primary language: [LANGUAGE]
- Main framework: [FRAMEWORK]
- Current task: [TASK_DESCRIPTION]

Design a workflow covering these phases:

## 1. Research Phase
Create 3 Gemini sidebar prompts I can use while reading documentation or
Stack Overflow answers to:
- Extract the exact code pattern I need
- Compare approaches mentioned on the page
- Identify gotchas or version-specific issues

## 2. Debug Phase
Create 3 Gemini sidebar prompts for when I'm looking at error pages,
GitHub issues, or log outputs to:
- Get a root cause analysis from the visible error
- Generate a fix based on the page context
- Find related issues I should check

## 3. Code Review Phase
Create 3 Gemini sidebar prompts for reviewing PRs or code files in
GitHub's web UI to:
- Summarize what the PR actually changes
- Spot potential bugs or security issues
- Suggest improvements with code examples

For each prompt:
- Make it copy-pasteable into Chrome's Gemini sidebar
- Reference "the content on this page" so Gemini uses page context
- Keep under 100 words (sidebar has limited input)
- Include expected output format

Output as a markdown checklist I can bookmark.
```

## When to Use

- Setting up Gemini Chrome for the first time
- Building repeatable browser-based dev workflows
- Teams adopting browser-native AI tools

## Example Output

The prompt generates 9 ready-to-use Gemini sidebar prompts organized by phase, plus a bookmark-friendly checklist format.

## Tips

- Works best on Chrome desktop (Mac/Windows/Chromebook Plus)
- Gemini sidebar can access Gmail, Drive, and YouTube context too
- Combine with tab comparison: open two approaches, ask Gemini to compare

---

> 💡 **Want the full version?** The [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app) includes 100+ production-ready resources including a complete Gemini Chrome Power User system with 25+ optimized prompts, multi-tab workflows, and integration with Drive/Gmail/Keep for full-stack browser development.
