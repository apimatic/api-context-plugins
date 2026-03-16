# APIMatic Context Plugins

**SDK-native API context, delivered directly into your AI coding assistant.**

[![Product Page](https://img.shields.io/badge/Product-Context%20Plugins-blue)](https://www.apimatic.io/product/context-plugins)
[![Available for Cursor](https://img.shields.io/badge/IDE-Cursor-orange)](https://www.apimatic.io/product/context-plugins)
[![Available for Claude Code](https://img.shields.io/badge/IDE-Claude%20Code-purple)](https://www.apimatic.io/product/context-plugins)

> 📖 **[View the full interactive documentation →](https://apimatic.github.io/api-context-plugins/README.html)**

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

## Example Prompts by Use Case

Copy-paste these directly into Cursor or Claude Code after installing a plugin.

### Getting started

```
Initialize the PayPal Server SDK in my Node.js app and make a test order creation call against the sandbox.
```

```
How do I authenticate with the Twilio API and send an SMS? Give me the full PHP setup including the SDK client and the send call.
```

```
Walk me through initializing the Slack API client in a Python script and posting a message to a channel.
```

### Framework-specific

**Next.js (TypeScript)**

```
I'm building a Next.js app. Integrate the PayPal Orders API to create and capture orders server-side. Use API routes for the backend and Smart Payment Buttons on the frontend.
```

```
Add Twilio SMS notifications to my Next.js app. Send a confirmation text to the customer after their order is captured. Use the TypeScript SDK and show me the API route and the send call.
```

**Laravel (PHP)**

```
I'm using Laravel. Integrate PayPal checkout — create an order on the backend, redirect the user to PayPal, then capture the payment on return. Use the PHP SDK.
```

```
I'm using Laravel. Show me how to send a Twilio SMS when a user registers. Include the PHP SDK setup, client initialization, and the controller code.
```

**ASP.NET Core (C#)**

```
I have an ASP.NET Core app. Integrate PayPal order creation and capture using the C# SDK. Show me the controller, the strongly-typed request models, and how to handle the capture response.
```

```
I have an ASP.NET Core app. Add Twilio webhook handling so I can receive delivery status callbacks when an SMS is sent. Show me the controller and signature validation.
```

**Django (Python)**

```
I'm building a Django app. Integrate the PayPal Orders API — show me the views for order creation and capture, the URL config, and the template that renders the PayPal button.
```

```
I have a Django app. Use the Slack Python SDK to post a message to a channel when a background Celery task completes. Show me the task code and the Slack client setup.
```

**Ruby on Rails**

```
I'm building a Ruby on Rails app. How do I post a Slack message to a channel when a background job finishes? Show me the initializer, the job code, and the Slack client call.
```

### Chaining multiple APIs

```
In my Next.js e-commerce app: (1) create a PayPal order when the user clicks Pay, (2) capture it after PayPal redirects back, and (3) send a Twilio SMS confirmation to the buyer. Show me the full flow across both SDKs in TypeScript.
```

```
I'm building a Laravel app. When a user completes a PayPal payment, post a Slack message to our #orders channel with the order ID, buyer name, and amount. Show me the capture handler and the Slack send call in PHP.
```

```
I have an ASP.NET Core app. After a PayPal order is captured, send a Twilio SMS to the buyer and post a summary to a Slack channel. Walk me through setting up all three integrations in C#.
```

### Debugging

```
My PayPal captureOrder is returning INSTRUMENT_DECLINED. What does this mean, how do I detect it from the TypeScript SDK response, and what should I show the user so they can retry?
```

```
I'm calling captureOrder and getting ORDER_ALREADY_CAPTURED on retry. How do I make this call idempotent using the PayPal TypeScript SDK?
```

```
I'm getting a "21211" error from Twilio when sending SMS. What does this error mean and how do I handle it gracefully with the PHP SDK?
```

```
My Slack message posts are failing intermittently with rate limit errors. How does the Python SDK expose rate limit information and what's the recommended retry pattern?
```

---

## Scenarios

### PayPal Instant Storefront

**What was built:** A full Node.js/Express storefront with product management, shareable checkout links per product, PayPal Smart Payment Buttons, server-side order creation and capture, and a payment history dashboard.

**The prompt:**

```
Build me a "PayPal Instant Storefront" app using the PayPal MCP server. The app has a setup
page where I enter my PayPal client-id and secret once, then a product creation form where I
enter a product name, description, price, currency, and upload or provide product images. When
I click "Generate Checkout Page" it creates a live, shareable checkout URL like /checkout/abc123
that anyone can open — they see the product details with images, price, description, and a
working PayPal Smart Payment Button. The payment flow should be fully server-side using the
PayPal Server SDK: backend creates the order when buyer clicks pay, captures it after approval,
and shows a confirmation page with order details. Include a dashboard showing all products,
their checkout links, and completed payments. Make it deployable with npm install and npm start.
```

**How the tools were used:**

| Step | Tool | Query | What it returned |
|------|------|-------|-----------------|
| 1 | `endpoint_search` | `ordersCreate` | TypeScript method signature and required body structure |
| 2 | `endpoint_search` | `captureOrder` | Capture contract, payer info extraction, capture ID location in response |
| 3 | `endpoint_search` | `getOrder` | Order retrieval details for the confirmation page |
| 4 | `model_search` | `AmountWithBreakdown` | Schema for correctly structuring item amounts and totals |
| 5 | `model_search` | `PurchaseUnitRequest` | Required fields for order line items |
| 6 | `ask` | SDK setup & auth | Client init, sandbox vs. live config, credential handling |
| 7 | `ask` | Smart Payment Buttons | Frontend button integration aligned to the SDK |
| 8 | `ask` | Deprecation guidance | Flagged `payer` and `application_context` as deprecated |
| 9 | `ask` | Capture & confirmation | Full create → approve → capture flow with payer info extraction |

**App outcome:**

- One-time credential setup page with live sandbox validation
- Product creation with name, description, price, currency, and image upload
- Unique shareable checkout URL per product (`/checkout/abc123`)
- Server-side order creation and capture — no client secrets exposed
- Confirmation page with order ID, buyer info, and capture details
- Dashboard with all products, total revenue, and payment history
- Mobile-responsive checkout pages
- Deployable with `npm install && npm start`

**Build time:** 10 min generation + 20 min testing = **30 minutes total**

![paypalsampleapp](https://github.com/user-attachments/assets/dc3e5b02-934e-44b5-9df9-20387557babe)


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
