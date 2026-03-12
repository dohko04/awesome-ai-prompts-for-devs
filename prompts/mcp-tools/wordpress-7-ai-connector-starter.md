# WordPress 7.0 AI Connector — Quick Start Prompt

> **Category:** MCP Tools / WordPress AI  
> **Works with:** GPT-5.4, Claude Opus 4.6, Gemini 3.1  
> **Updated:** March 2026  

## Why This Matters

WordPress 7.0 (releasing April 9, 2026) introduces **AI Connectors** — a native `php-ai-client` library that lets any plugin use OpenAI, Claude, or Gemini through a single centralized API key. No more per-plugin key management. Plus, there's an **MCP Adapter** so AI assistants can discover and invoke WordPress capabilities as tools.

This is the biggest WordPress architecture change in years. ~40% of the web runs WordPress. If you build WP plugins, you need to be ready.

## The Prompt

```
You are a WordPress plugin developer preparing for WordPress 7.0 AI Connectors (releasing April 9, 2026).

CONTEXT:
- WordPress 7.0 introduces Settings > Connectors: centralized API key storage for OpenAI, Anthropic (Claude), Google (Gemini)
- The `php-ai-client` package provides a standard PHP interface: `wp_ai_client_prompt()`
- Three provider plugins available: OpenAI, Google, Anthropic
- An MCP Adapter plugin exposes WordPress capabilities (posts, media, settings) as MCP tools/resources
- Keys are stored once, shared across all plugins — no more duplicate key fields

MY PLUGIN: [Describe your existing or planned WordPress plugin]
CURRENT AI INTEGRATION: [None / Custom API calls / Third-party SDK]

TASKS:
1. Show me how to migrate from direct API calls to `wp_ai_client_prompt()` 
2. Create a minimal working example that:
   - Checks if a connector is configured
   - Sends a prompt through the unified API
   - Handles the response with proper error handling
3. List the 3 most valuable AI features I should add to my plugin using Connectors
4. Show the hook/filter pattern for letting users choose which AI provider to use

OUTPUT FORMAT:
- Working PHP code snippets (copy-paste ready)
- Each snippet under 50 lines
- Comments explaining WP 7.0-specific APIs
```

## Example Output (What You'll Get)

The AI will generate:
- Migration code from raw `wp_remote_post()` to `wp_ai_client_prompt()`
- Provider detection: `if ( function_exists('wp_ai_client_prompt') )`
- Error handling patterns for missing keys / rate limits
- Feature suggestions based on your plugin type

## Real-World Use Case

If you have a SEO plugin that currently calls OpenAI directly:

```php
// OLD WAY (pre-7.0) — your plugin manages its own API key
$response = wp_remote_post('https://api.openai.com/v1/chat/completions', [
    'headers' => ['Authorization' => 'Bearer ' . get_option('my_plugin_openai_key')],
    'body' => json_encode(['model' => 'gpt-5.4', 'messages' => $messages])
]);

// NEW WAY (WP 7.0) — centralized connector handles auth
$response = wp_ai_client_prompt('Generate SEO meta description for: ' . $post_title);
```

## Limitations of This Free Version

This starter covers the basics. The **PRO version** includes:
- Full MCP Adapter integration (expose your plugin as AI tools)
- Multi-provider fallback chain (OpenAI → Claude → Gemini)
- Token cost tracking and budget controls per plugin
- Production deployment checklist for WP 7.0 migration
- Streaming response handler for real-time UX

👉 **Get the full WordPress 7.0 AI Plugin Pipeline:** [ai-dev-toolkit](https://ai-dev-toolkit-five.vercel.app)

---

*Part of [awesome-ai-prompts-for-devs](https://github.com/dohko04/awesome-ai-prompts-for-devs) — Free AI prompts for developers*
