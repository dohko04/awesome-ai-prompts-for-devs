# ✨ The Prompt Improver

> **When to use:** You have a prompt that kinda works but you want it to be great.

## Prompt Template

```
Improve this prompt I've been using:

[paste your current prompt]

What I want it to do: [expected output]
What it actually produces: [current issues with output]

Please:
1. Rewrite the prompt to be more effective
2. Explain each change you made and why
3. Add structure (numbered steps, output format)
4. Include constraints to prevent common failure modes
5. Give me 3 variations for different scenarios
```

## Example Output

> **Changes made:**
> 1. Added role context ("You are a senior backend engineer") — LLMs perform better with persona framing
> 2. Added explicit output format — prevents rambling responses
> 3. Added "Think step by step" — improves reasoning accuracy by ~15% per research
> 4. Added negative constraints ("Do NOT include boilerplate") — prevents common filler
> 5. Added example of desired output — few-shot learning beats zero-shot

---

> 💡 **Want 100+ more prompts like this?** → [AI Dev Toolkit ($9)](https://ai-dev-toolkit-five.vercel.app)
