# APIMatic Context Plugins

**SDK-native API context, delivered directly into your AI coding assistant.**

[![Product Page](https://img.shields.io/badge/Product-Context%20Plugins-blue)](https://www.apimatic.io/product/context-plugins)
[![Available for Cursor](https://img.shields.io/badge/IDE-Cursor-orange)](https://www.apimatic.io/product/context-plugins)
[![Available for Claude Code](https://img.shields.io/badge/IDE-Claude%20Code-purple)](https://www.apimatic.io/product/context-plugins)

---

## Quick Install

| Cursor | Claude Code |
|--------|-------------|
| [Install](https://www.apimatic.io/product/context-plugins?ide=cursor) | [Install](https://www.apimatic.io/product/context-plugins?ide=claudeCode) |

---

## What is a Context Plugin?

A Context Plugin is a one-click MCP Server that delivers SDK-generated API context directly into AI-assisted IDEs like Cursor and Claude Code.

When a developer asks their AI assistant to "integrate the payments API," it normally guesses — pulling from outdated training data or generic patterns that don't match your SDK. A Context Plugin solves this by giving the AI assistant *authoritative*, *version-aware*, *SDK-native* context at the exact moment it's needed.

No browser tab switching. No hallucinated endpoints. Just correct integration code on the first attempt.

---

## Supported APIs

| API | Description |
|-----|-------------|
| **Adyen API** | Payment processing: retrieve payment methods, create orders, manage stored payment tokens |
| **Google Maps APIs** | Location services: geocoding, directions, distance matrix, elevation, roads, and places |
| **PayPal Server SDK** | Payment flows: orders, payments, vault, transaction search, and subscriptions |
| **PayQuicker API** | Payment and financial services: program agreements, bank accounts, spendback quotes |
| **PostNL Ecommerce APIs** | Postal and logistics: delivery dates, barcodes, shipment status, parcel creation |
| **Slack API** | Workspace automation: OAuth bots, messaging, conversation management |
| **Spotify Web API** | Music and podcasts: library management, playback control, discovery |
| **Tesla Fleet Management API** | Vehicle and fleet operations: charging history, vehicle commands, energy management |
| **Tesser API Portal** | Digital payments: payment intents, onchain payments, app management |
| **Twilio API** | Communications: SMS, voice, video, and verification services |

---

## Supported Languages

| Language | Identifier |
|----------|-----------|
| TypeScript | `typescript` |
| C# | `csharp` |
| Python | `python` |
| Java | `java` |
| Go | `go` |
| PHP | `php` |
| Ruby | `ruby` |

---

## What the Plugin Gives Your AI Assistant

| Tool | Developer task it enables |
|------|--------------------------|
| `fetch_api` | **"What APIs can I use?"** — Lists all available APIs with their name, key, and description. |
| `ask` | **"How do I integrate this?"** — Step-by-step integration guidance, auth setup, SDK code samples. |
| `model_search` | **"What does this model look like?"** — Full SDK model definition and typed properties by name. |
| `endpoint_search` | **"What parameters does this method take?"** — Endpoint method description, inputs, and response shape. |

---

## From Prompt to Code: How the Tools Work Together

**Your prompt:** *"Add Twilio SMS notifications to my Next.js app. Send a text when an order ships."*

| Step | Tool called | What it returns |
|------|-------------|----------------|
| 1 | `fetch_api` (`language=typescript`) | Discovers Twilio is available; returns its `key` |
| 2 | `ask` | Returns exact SDK setup code with auth configuration |
| 3 | `endpoint_search` (`query=createMessage`) | Method signature, required parameters, auth requirements |
| 4 | `model_search` (`query=CreateMessageRequest`) | Full typed request model with every available field |
| 5 | `ask` | Webhook handling code for delivery status callbacks in Next.js |

---

## PayPal Checkout Integration: A Complete Walkthrough

With the PayPal Context Plugin installed, one prompt does it all:

```
Integrate PayPal in my checkout page
```

The plugin calls 9 tools automatically — `endpoint_search` for `ordersCreate`, `captureOrder`, and `getOrder`; `model_search` for `AmountWithBreakdown` and `PurchaseUnitRequest`; and `ask` for SDK setup, Smart Payment Buttons, deprecation guidance, and the full capture flow.

**Works across frameworks:**

| Framework | Language | Generated code includes |
|-----------|----------|------------------------|
| **Next.js** | TypeScript | API routes for order create/capture, Smart Payment Button component, confirmation page |
| **Laravel** | PHP | Controller methods, Blade views with PayPal JS SDK, webhook handling |
| **ASP.NET Core** | C# | Controllers, strongly-typed request models, order capture middleware |
| **Express** | TypeScript | Checkout routes, Multer image upload, payment history endpoint |
| **Django** | Python | Views for order creation and capture, template-rendered checkout pages |

> 📹 Integration demo video — coming soon.

---

## Example Prompts to Try

### Getting started

```
Set up the Spotify TypeScript SDK and fetch my top 5 tracks. Show me the complete client initialization and the API call.
```

```
How do I authenticate with the Twilio API and send an SMS? Give me the full PHP setup including the SDK client and the send call.
```

```
Walk me through initializing the Slack API client in a Python script and posting a message to a channel.
```

### Framework-specific

```
I'm building a Next.js app. Integrate the Google Maps Places API to search for nearby restaurants and display them on a page. Use the TypeScript SDK.
```

```
I'm using Laravel. Show me how to send a Twilio SMS when a user registers. Include the PHP SDK setup, client initialization, and the controller code.
```

```
I have an ASP.NET Core app. Add Twilio webhook handling so I can receive delivery status callbacks when an SMS is sent.
```

### Full integrations

```
I want to add real-time order shipping notifications to my Next.js store. Use Twilio to send an SMS when the order status changes to "shipped". Show me the full integration: SDK setup, the correct endpoint and its parameters, and the TypeScript code.
```

```
In my ASP.NET Core app, I want to geocode user addresses using Google Maps and cache the results. Look up the geocode endpoint and response model, then generate the C# code including error handling.
```

### Debugging

```
My Spotify API call is returning 401. What OAuth flow should I be using and how does the TypeScript SDK handle token refresh automatically?
```

```
My Slack message posts are failing intermittently with rate limit errors. How does the Python SDK expose rate limit information and what's the recommended retry pattern?
```

---

## Why Not Just Use LLMs.txt or Documentation?

| Approach | Problem |
|----------|---------|
| Developer portal | Developers visit once, then build in their IDE — the gap creates friction |
| LLMs.txt | Static, machine-readable docs — no SDK-native patterns, no idiomatic code |
| AI without context | Trained on historical data — confidently generates outdated or incorrect code |
| **Context Plugin** | SDK-generated, version-aware context delivered where developers actually code |

---

## Measured Results

- **2× faster integration** compared to working from documentation alone
- **48% lower development cost**
- **65% reduction in context usage**
- **~Zero hallucinations** — no fabricated endpoints or non-existent SDK methods

→ [Read the full case study](https://www.apimatic.io/product/context-plugins/case-study)

---

## How APIMatic Generates a Context Plugin

APIMatic takes your OpenAPI specification through the same SDK generation pipeline it uses to produce idiomatic, type-safe SDKs in 10+ languages. The resulting MCP server exposes SDK documentation and integration patterns as structured tool responses that AI assistants can consume natively.

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

Found an issue or want to request an API? [Open an issue](../../issues) or reach out at [support@apimatic.io](mailto:support@apimatic.io).

---

## Learn More

- [Product page](https://www.apimatic.io/product/context-plugins)
- [Blog: From API Portals to Cursor](https://www.apimatic.io/blog/from-api-portals-to-cursor)
- [APIMatic Documentation](https://docs.apimatic.io/)
- [Free Trial](https://www.apimatic.io/free-trial)
