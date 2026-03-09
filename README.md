# APIMatic Context Plugins

**SDK-native API context, delivered directly into your AI coding assistant.**

[![Product Page](https://img.shields.io/badge/Product-Context%20Plugins-blue)](https://www.apimatic.io/product/context-plugins)
[![Available for Cursor](https://img.shields.io/badge/IDE-Cursor-orange)](https://www.apimatic.io/product/context-plugins)
[![Available for VS Code](https://img.shields.io/badge/IDE-VS%20Code-blue)](https://www.apimatic.io/product/context-plugins)
[![Available for Claude Code](https://img.shields.io/badge/IDE-Claude%20Code-purple)](https://www.apimatic.io/product/context-plugins)

---

## What is a Context Plugin?

A Context Plugin is a one-click MCP Server that delivers SDK-generated API context directly into AI-assisted IDEs like Cursor, VS Code, and Claude Code.

When a developer asks their AI assistant to "integrate the payments API," it normally guesses — pulling from outdated training data or generic patterns that don't match your SDK. A Context Plugin solves this by giving the AI assistant *authoritative*, *version-aware*, *SDK-native* context at the exact moment it's needed.

No browser tab switching. No hallucinated endpoints. Just correct integration code on the first attempt.

---

## Try It Now

One-click install into your IDE:

| API | Cursor | VS Code | Claude Code |
|-----|--------|---------|-------------|
| **Spotify Web API** | [Install](https://spotify-poc-apimatic.pages.dev/#/typescript/sample-app/music-dna-card-generator-vibe-coded?ide=cursor&isContextPlugin=true) | [Install](https://spotify-poc-apimatic.pages.dev/#/typescript/sample-app/music-dna-card-generator-vibe-coded?ide=vscode&isContextPlugin=true) | [Install](https://spotify-poc-apimatic.pages.dev/#/typescript/sample-app/music-dna-card-generator-vibe-coded?ide=claudeCode&isContextPlugin=true) |
| **Google Maps API** | [Install](https://gm-poc-apimatic.pages.dev/#/typescript/sample-app/spin-the-wheel-vibe-coded?ide=cursor&isContextPlugin=true) | [Install](https://gm-poc-apimatic.pages.dev/#/typescript/sample-app/spin-the-wheel-vibe-coded?ide=vscode&isContextPlugin=true) | [Install](https://gm-poc-apimatic.pages.dev/#/typescript/sample-app/spin-the-wheel-vibe-coded?ide=claudeCode&isContextPlugin=true) |
| **Twilio APIs** | [Install](https://twillo-poc-apimatic.pages.dev/#/typescript/sample-app/birthdaybuzz-vibe-coded?ide=cursor&isContextPlugin=true) | [Install](https://twillo-poc-apimatic.pages.dev/#/typescript/sample-app/birthdaybuzz-vibe-coded?ide=vscode&isContextPlugin=true) | [Install](https://twillo-poc-apimatic.pages.dev/#/typescript/sample-app/birthdaybuzz-vibe-coded?ide=claudeCode&isContextPlugin=true) |
| **Slack API** | [Install](https://slack-poc-apimatic.pages.dev/#/typescript/sample-app/slack-analytics-dashboard-vibe-coded?ide=cursor&isContextPlugin=true) | [Install](https://slack-poc-apimatic.pages.dev/#/typescript/sample-app/slack-analytics-dashboard-vibe-coded?ide=vscode&isContextPlugin=true) | [Install](https://slack-poc-apimatic.pages.dev/#/typescript/sample-app/slack-analytics-dashboard-vibe-coded?ide=claudeCode&isContextPlugin=true) |

---

## What the Plugin Gives Your AI Assistant

Once installed, the plugin exposes four tools to your AI coding assistant:

| Tool | What it does |
|------|-------------|
| **Fetch API** | Retrieves SDK-generated documentation for a specific endpoint — including request/response structure, auth requirements, and idiomatic code samples |
| **Ask** | Answers integration questions using SDK context and getting started guides. Works for framework-specific questions like "How do I call this endpoint from a Next.js app?" or "What does the Laravel SDK client initialization look like?" |
| **Search Endpoint** | Finds the right endpoint(s) to use for a given task described in natural language |
| **Search** | General search across all available API context — useful when you're not sure which endpoint or SDK method you need |

---

## Example Prompts to Try

The best way to experience Context Plugins is to paste these prompts directly into Cursor, VS Code, or Claude Code after installing a plugin.

### Getting started with an API

```
Set up a Spotify API client and fetch my top 5 tracks. Show me the TypeScript code using the official SDK.
```

```
How do I authenticate with the Twilio API and send an SMS message?
```

### Framework-specific integration

```
I'm building a Next.js app. How do I call the Google Maps Places API to get nearby restaurants?
```

```
Show me how to integrate the Slack API in a Laravel application to post a message to a channel.
```

```
What's the correct way to handle Twilio webhook callbacks in an ASP.NET Core app?
```

### Working with multiple APIs

```
I want to build a birthday reminder app that sends a Twilio SMS and posts to a Slack channel. Walk me through integrating both APIs.
```

```
How do I combine the Spotify and Slack APIs to post my currently playing track to a Slack channel?
```

### Debugging and error handling

```
My Spotify API call is returning a 401. What auth flow should I be using and how does the SDK handle token refresh?
```

```
What errors should I handle when calling the Google Maps Directions API, and what does the SDK error type look like?
```

---

## Why Not Just Use LLMs.txt or Documentation?

| Approach | Problem |
|----------|---------|
| Developer portal | Developers visit once, then build in their IDE — the gap between the two creates friction |
| LLMs.txt | Static, machine-readable docs — no SDK-native patterns, no idiomatic code |
| AI without context | Trained on historical data — confidently generates outdated or incorrect integration code |
| **Context Plugin** | SDK-generated, version-aware context delivered where developers actually code |

---

## Measured Results

Tested against legacy code migration and new API integration in two production-grade applications:

- **2× faster integration** compared to working from documentation alone
- **48% lower development cost**
- **65% reduction in context usage** — the AI gets it done with fewer tokens
- **~Zero hallucinations** — no fabricated endpoints or non-existent SDK methods

From the internal blog post benchmark: token efficiency increases by 37%, integration success on complex APIs hits 83%, and code quality scores run ~30% higher on average with roughly 70% fewer security issues per thousand lines of code.

→ [Read the full case study](https://www.apimatic.io/product/context-plugins/case-study)

---

## How APIMatic Generates a Context Plugin

APIMatic takes your OpenAPI specification through the same SDK generation pipeline it uses to produce idiomatic, type-safe SDKs in 10+ languages. The resulting MCP server exposes the SDK documentation and integration patterns as structured tool responses that AI assistants can consume natively.

This means the context the AI receives is:
- Derived from actual generated SDK code, not raw documentation
- Inclusive of idiomatic patterns, typed models, and error handling
- Aligned to the current version of your API spec

For API providers: [request a demo](https://www.apimatic.io/request-demo) to generate a Context Plugin for your own API.

---

## Repository Structure

```
api-context-plugins/
├── plugins/            # Per-API plugin configurations and manifests
├── tools/              # MCP tool definitions (fetch, ask, search-endpoint, search)
├── docs/               # Implementation guides and integration references
└── examples/           # Sample apps and usage walkthroughs per API
```

---

## Contributing

Found an issue with a specific plugin or want to request an API? [Open an issue](../../issues) or reach out at [support@apimatic.io](mailto:support@apimatic.io).

---

## Learn More

- [Product page](https://www.apimatic.io/product/context-plugins)
- [Blog: From API Portals to Cursor](https://www.apimatic.io/blog/from-api-portals-to-cursor)
- [APIMatic Documentation](https://docs.apimatic.io/)
- [Free Trial](https://www.apimatic.io/free-trial)