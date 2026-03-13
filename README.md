<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>APIMatic Context Plugins</title>
<style>
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
  body { font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif; background: #fff; color: #111; font-size: 15px; line-height: 1.7; max-width: 860px; margin: 0 auto; padding: 2rem 2rem 4rem; }
  h1 { font-size: 26px; font-weight: 600; margin: 0 0 8px; }
  h2 { font-size: 20px; font-weight: 600; margin: 2.5rem 0 0.75rem; }
  h3 { font-size: 16px; font-weight: 600; margin: 1.5rem 0 0.5rem; }
  p { color: #444; margin: 0 0 1rem; }
  a { color: #185FA5; text-decoration: none; } a:hover { text-decoration: underline; }
  code { font-family: 'SFMono-Regular', Consolas, monospace; font-size: 13px; background: #f4f4f4; padding: 2px 6px; border-radius: 4px; }
  pre { background: #f4f4f4; border: 1px solid #e8e8e8; border-radius: 8px; padding: 1rem; overflow-x: auto; margin: 0.5rem 0 1rem; }
  pre code { background: none; padding: 0; font-size: 13px; color: #444; }
  hr { border: none; border-top: 1px solid #e8e8e8; margin: 2rem 0; }
  table { width: 100%; border-collapse: collapse; font-size: 14px; margin: 0.75rem 0 1.25rem; }
  th { text-align: left; font-weight: 600; font-size: 13px; color: #666; padding: 8px 12px; border-bottom: 1px solid #e8e8e8; background: #f9f9f9; }
  td { padding: 8px 12px; border-bottom: 1px solid #f0f0f0; color: #444; vertical-align: top; }
  tr:last-child td { border-bottom: none; }
  ul { margin: 0.25rem 0 1rem; padding-left: 1.25rem; }
  li { font-size: 15px; line-height: 1.7; color: #444; margin-bottom: 4px; }
  li strong { color: #111; }
  blockquote { margin: 0.75rem 0; padding: 0.75rem 1rem; background: #f9f9f9; border-left: 3px solid #ddd; border-radius: 0 6px 6px 0; color: #666; font-size: 14px; }
  em { color: #555; }

  .badges { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 1.25rem; }
  .badge { font-size: 12px; font-weight: 500; padding: 4px 10px; border-radius: 6px; border: 1px solid #ddd; color: #555; background: #f4f4f4; }
  .badge.blue { background: #E6F1FB; color: #0C447C; border-color: #85B7EB; }
  .badge.orange { background: #FAEEDA; color: #633806; border-color: #EF9F27; }
  .badge.purple { background: #EEEDFE; color: #3C3489; border-color: #AFA9EC; }

  .install-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 12px; margin: 0.75rem 0 1.25rem; }
  .install-btn { display: flex; align-items: center; justify-content: space-between; padding: 12px 16px; background: #fff; border: 1px solid #ddd; border-radius: 8px; text-decoration: none; color: #111; }
  .install-btn:hover { background: #f9f9f9; text-decoration: none; }
  .install-btn .ide-tag { font-size: 12px; color: #888; font-weight: 400; }
  .install-btn .btn-label { font-size: 14px; font-weight: 500; }
  .install-btn .arrow { font-size: 12px; color: #bbb; }

  .section-card { background: #fff; border: 1px solid #e8e8e8; border-radius: 10px; padding: 1.25rem 1.5rem; margin-bottom: 1rem; }
  .tool-card { display: flex; gap: 12px; padding: 12px 0; border-bottom: 1px solid #f0f0f0; }
  .tool-card:last-child { border-bottom: none; }
  .tool-name { font-family: monospace; font-size: 13px; font-weight: 600; color: #111; min-width: 130px; padding-top: 2px; }
  .tool-task-q { font-size: 14px; font-weight: 600; color: #111; margin-bottom: 2px; }
  .tool-task-desc { font-size: 13px; color: #666; line-height: 1.6; }

  .step-row { display: flex; gap: 12px; align-items: flex-start; padding: 10px 0; border-bottom: 1px solid #f0f0f0; font-size: 14px; }
  .step-row:last-child { border-bottom: none; }
  .step-num { width: 24px; height: 24px; border-radius: 50%; background: #f4f4f4; border: 1px solid #e0e0e0; display: flex; align-items: center; justify-content: center; font-size: 11px; font-weight: 600; color: #666; flex-shrink: 0; margin-top: 1px; }
  .step-tool { font-family: monospace; font-size: 12px; color: #555; min-width: 120px; padding-top: 3px; }
  .step-desc { color: #444; line-height: 1.5; flex: 1; }

  .prompt-box { background: #f4f4f4; border: 1px solid #e8e8e8; border-radius: 8px; padding: 1rem 1.25rem; margin: 0.75rem 0 1.25rem; font-family: monospace; font-size: 13px; color: #444; line-height: 1.7; }
  .prompt-example { background: #f9f9f9; border: 1px solid #eee; border-radius: 6px; padding: 10px 14px; margin-bottom: 8px; font-family: monospace; font-size: 12.5px; color: #555; line-height: 1.6; }

  .framework-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(150px, 1fr)); gap: 10px; margin: 0.75rem 0 1.25rem; }
  .fw-card { background: #f9f9f9; border: 1px solid #eee; border-radius: 8px; padding: 12px 14px; }
  .fw-name { font-size: 14px; font-weight: 600; margin-bottom: 2px; }
  .fw-lang { font-size: 12px; color: #888; margin-bottom: 6px; }
  .fw-desc { font-size: 12px; color: #666; line-height: 1.5; }

  .results-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin: 0.75rem 0 1.25rem; }
  .result-item { background: #f9f9f9; border-radius: 8px; padding: 12px 14px; display: flex; align-items: flex-start; gap: 10px; }
  .result-metric { font-size: 22px; font-weight: 600; color: #111; min-width: 55px; }
  .result-desc { font-size: 13px; color: #666; line-height: 1.5; }

  .why-row { display: flex; gap: 12px; padding: 10px 0; border-bottom: 1px solid #f0f0f0; font-size: 14px; align-items: flex-start; }
  .why-row:last-child { border-bottom: none; }
  .why-approach { font-weight: 600; min-width: 140px; color: #111; }
  .why-problem { color: #555; flex: 1; }
  .why-row.highlight .why-approach { color: #185FA5; }
  .why-row.highlight .why-problem { color: #111; font-weight: 500; }

  .link-list { display: flex; flex-wrap: wrap; gap: 8px; margin: 0.5rem 0 1rem; }
  .link-pill { font-size: 13px; padding: 5px 12px; background: #f4f4f4; border: 1px solid #e0e0e0; border-radius: 6px; color: #185FA5; text-decoration: none; }
  .link-pill:hover { background: #eaf1fb; text-decoration: none; }

  .repo-block { background: #f4f4f4; border-radius: 8px; padding: 1rem 1.25rem; margin: 0.75rem 0; font-family: monospace; font-size: 13px; color: #555; line-height: 2; }
  .repo-dir { color: #111; font-weight: 600; }
  .repo-comment { color: #999; font-size: 12px; }

  @media (max-width: 600px) {
    .install-grid, .results-grid { grid-template-columns: 1fr; }
    .tool-card { flex-direction: column; gap: 4px; }
    .step-tool { min-width: 80px; }
  }
</style>
</head>
<body>

<div style="margin-bottom: 1.5rem;">
  <h1>APIMatic Context Plugins</h1>
  <p style="font-size:16px;margin-bottom:1rem;">SDK-native API context, delivered directly into your AI coding assistant.</p>
  <div class="badges">
    <span class="badge blue">Product: Context Plugins</span>
    <span class="badge orange">IDE: Cursor</span>
    <span class="badge purple">IDE: Claude Code</span>
  </div>
</div>

<hr>

<h2>What is a Context Plugin?</h2>
<p>A Context Plugin is a one-click MCP Server that delivers SDK-generated API context directly into AI-assisted IDEs like Cursor and Claude Code.</p>
<p>When a developer asks their AI assistant to "integrate the payments API," it normally guesses — pulling from outdated training data or generic patterns that don't match your SDK. A Context Plugin solves this by giving the AI assistant <em>authoritative</em>, <em>version-aware</em>, <em>SDK-native</em> context at the exact moment it's needed.</p>
<p>No browser tab switching. No hallucinated endpoints. Just correct integration code on the first attempt.</p>

<hr>

<h2>Try it now</h2>
<div class="install-grid">
  <a class="install-btn" href="https://www.apimatic.io/product/context-plugins?ide=cursor">
    <div><div class="btn-label">Install for Cursor</div><div class="ide-tag">One-click install</div></div>
    <span class="arrow">↗</span>
  </a>
  <a class="install-btn" href="https://www.apimatic.io/product/context-plugins?ide=claudeCode">
    <div><div class="btn-label">Install for Claude Code</div><div class="ide-tag">One-click install</div></div>
    <span class="arrow">↗</span>
  </a>
</div>

<hr>

<h2>Supported APIs</h2>
<table>
  <tr><th>API</th><th>Description</th></tr>
  <tr><td><strong>Adyen API</strong></td><td>Payment processing: retrieve payment methods, create orders, manage stored payment tokens</td></tr>
  <tr><td><strong>Google Maps APIs</strong></td><td>Location services: geocoding, directions, distance matrix, elevation, roads, and places</td></tr>
  <tr><td><strong>PayPal Server SDK</strong></td><td>Payment flows: orders, payments, vault, transaction search, and subscriptions</td></tr>
  <tr><td><strong>PayQuicker API</strong></td><td>Payment and financial services: program agreements, bank accounts, spendback quotes</td></tr>
  <tr><td><strong>PostNL Ecommerce APIs</strong></td><td>Postal and logistics: delivery dates, barcodes, shipment status, parcel creation</td></tr>
  <tr><td><strong>Slack API</strong></td><td>Workspace automation: OAuth bots, messaging, conversation management</td></tr>
  <tr><td><strong>Spotify Web API</strong></td><td>Music and podcasts: library management, playback control, discovery</td></tr>
  <tr><td><strong>Tesla Fleet Management API</strong></td><td>Vehicle and fleet operations: charging history, vehicle commands, energy management</td></tr>
  <tr><td><strong>Tesser API Portal</strong></td><td>Digital payments: payment intents, onchain payments, app management</td></tr>
  <tr><td><strong>Twilio API</strong></td><td>Communications: SMS, voice, video, and verification services</td></tr>
</table>

<hr>

<h2>Supported languages</h2>
<table>
  <tr><th>Language</th><th>Identifier</th></tr>
  <tr><td>TypeScript</td><td><code>typescript</code></td></tr>
  <tr><td>C#</td><td><code>csharp</code></td></tr>
  <tr><td>Python</td><td><code>python</code></td></tr>
  <tr><td>Java</td><td><code>java</code></td></tr>
  <tr><td>Go</td><td><code>go</code></td></tr>
  <tr><td>PHP</td><td><code>php</code></td></tr>
  <tr><td>Ruby</td><td><code>ruby</code></td></tr>
</table>

<hr>

<h2>What the plugin gives your AI assistant</h2>
<div class="section-card">
  <div class="tool-card">
    <div class="tool-name"><code>fetch_api</code></div>
    <div>
      <div class="tool-task-q">"What APIs can I use?"</div>
      <div class="tool-task-desc">Lists all available APIs with their name, key, and description. Your AI assistant calls this first to discover which APIs are available for your project's language.</div>
    </div>
  </div>
  <div class="tool-card">
    <div class="tool-name"><code>ask</code></div>
    <div>
      <div class="tool-task-q">"How do I integrate this?"</div>
      <div class="tool-task-desc">Chat with API Copilot for step-by-step integration guidance: authentication setup, client initialization, feature behavior, framework-specific patterns, and idiomatic SDK code samples.</div>
    </div>
  </div>
  <div class="tool-card">
    <div class="tool-name"><code>model_search</code></div>
    <div>
      <div class="tool-task-q">"What does this model look like?"</div>
      <div class="tool-task-desc">Returns an SDK model's full definition and typed properties by name. Call this before writing code that constructs request bodies or reads response objects.</div>
    </div>
  </div>
  <div class="tool-card">
    <div class="tool-name"><code>endpoint_search</code></div>
    <div>
      <div class="tool-task-q">"What parameters does this method take?"</div>
      <div class="tool-task-desc">Returns an SDK endpoint method's description, input parameters, and response shape by method name.</div>
    </div>
  </div>
</div>

<hr>

<h2>From prompt to code: how the tools work together</h2>
<p>The four tools chain together in a natural integration workflow. Here's what happens under the hood for a real task:</p>
<p style="font-size:14px;margin-bottom:0.75rem;">Prompt: <em>"Add Twilio SMS notifications to my Next.js app. Send a text when an order ships."</em></p>
<div class="section-card">
  <div class="step-row"><div class="step-num">1</div><div class="step-tool"><code>fetch_api</code></div><div class="step-desc">Discovers Twilio is available; returns its <code>key</code></div></div>
  <div class="step-row"><div class="step-num">2</div><div class="step-tool"><code>ask</code></div><div class="step-desc">Returns exact SDK setup code with auth configuration for the Twilio TypeScript client</div></div>
  <div class="step-row"><div class="step-num">3</div><div class="step-tool"><code>endpoint_search</code></div><div class="step-desc">Returns the method signature, required parameters, and auth requirements for <code>createMessage</code></div></div>
  <div class="step-row"><div class="step-num">4</div><div class="step-tool"><code>model_search</code></div><div class="step-desc">Returns the full typed <code>CreateMessageRequest</code> model with every available field</div></div>
  <div class="step-row"><div class="step-num">5</div><div class="step-tool"><code>ask</code></div><div class="step-desc">Returns webhook handling code aligned to the Twilio SDK for delivery status callbacks in Next.js</div></div>
</div>
<p style="font-size:14px;">Each step completes in a single tool call. Your AI assistant handles the orchestration — you describe the goal, and it picks the right tool at the right time.</p>

<hr>

<h2>PayPal checkout integration: a complete walkthrough</h2>
<p>Here's exactly what happens when a developer uses the PayPal Context Plugin to integrate a checkout flow — from a single prompt to working code, across real frameworks.</p>

<h3>The prompt</h3>
<p style="font-size:14px;">With the PayPal Context Plugin installed, you describe what you want in plain language:</p>
<div class="prompt-box">Integrate PayPal in my checkout page</div>
<p style="font-size:14px;">That's it. The plugin handles looking up the right endpoints, schemas, and SDK patterns automatically.</p>

<h3>What the plugin does</h3>
<p style="font-size:14px;">Behind the scenes, the AI assistant calls three tools in sequence — no documentation tab, no guessing:</p>
<div class="section-card">
  <div class="step-row"><div class="step-num">1</div><div class="step-tool"><code>endpoint_search</code></div><div class="step-desc">TypeScript method signature and required body structure for creating an order (<code>ordersCreate</code>)</div></div>
  <div class="step-row"><div class="step-num">2</div><div class="step-tool"><code>endpoint_search</code></div><div class="step-desc">Capture endpoint contract, how to extract payer info and capture IDs from the response (<code>captureOrder</code>)</div></div>
  <div class="step-row"><div class="step-num">3</div><div class="step-tool"><code>endpoint_search</code></div><div class="step-desc">Order retrieval details for showing a confirmation page (<code>getOrder</code>)</div></div>
  <div class="step-row"><div class="step-num">4</div><div class="step-tool"><code>model_search</code></div><div class="step-desc">Exact model schema to correctly structure item amounts and totals (<code>AmountWithBreakdown</code>)</div></div>
  <div class="step-row"><div class="step-num">5</div><div class="step-tool"><code>model_search</code></div><div class="step-desc">Required fields for order line items (<code>PurchaseUnitRequest</code>)</div></div>
  <div class="step-row"><div class="step-num">6</div><div class="step-tool"><code>ask</code></div><div class="step-desc">Client initialization, sandbox vs. live config, credential handling</div></div>
  <div class="step-row"><div class="step-num">7</div><div class="step-tool"><code>ask</code></div><div class="step-desc">Frontend button integration code aligned to the SDK (Smart Payment Buttons)</div></div>
  <div class="step-row"><div class="step-num">8</div><div class="step-tool"><code>ask</code></div><div class="step-desc">Flags deprecated fields (<code>payer</code>, <code>application_context</code>) before you hit them</div></div>
  <div class="step-row"><div class="step-num">9</div><div class="step-tool"><code>ask</code></div><div class="step-desc">Full create → approve → capture flow with payer info extraction and confirmation display</div></div>
</div>

<h3>What you get</h3>
<ul>
  <li><strong>Correct endpoint signatures</strong> — <code>createOrder</code>, <code>captureOrder</code>, and <code>getOrder</code> matched to the current SDK version</li>
  <li><strong>Typed request models</strong> — <code>OrderRequest</code>, <code>PurchaseUnitRequest</code>, <code>AmountWithBreakdown</code> with all required fields</li>
  <li><strong>Deprecation-safe code</strong> — fields like <code>payer</code> and <code>application_context</code> are avoided automatically</li>
  <li><strong>Idiomatic patterns</strong> — server-side order creation, client-side button rendering, and capture flow done the right way</li>
</ul>

<h3>Framework examples</h3>
<p style="font-size:14px;">The same prompt works across your stack. Here's what gets generated per framework:</p>
<div class="framework-grid">
  <div class="fw-card"><div class="fw-name">Next.js</div><div class="fw-lang">TypeScript</div><div class="fw-desc">API routes for order create/capture, Smart Payment Button component, confirmation page</div></div>
  <div class="fw-card"><div class="fw-name">Laravel</div><div class="fw-lang">PHP</div><div class="fw-desc">Controller methods for the order flow, Blade views with PayPal JS SDK, webhook handling</div></div>
  <div class="fw-card"><div class="fw-name">ASP.NET Core</div><div class="fw-lang">C#</div><div class="fw-desc">Controllers, strongly-typed request models, order capture middleware</div></div>
  <div class="fw-card"><div class="fw-name">Express</div><div class="fw-lang">TypeScript</div><div class="fw-desc">Checkout routes, Multer image upload, payment history endpoint</div></div>
  <div class="fw-card"><div class="fw-name">Django</div><div class="fw-lang">Python</div><div class="fw-desc">Views for order creation and capture, template-rendered checkout pages</div></div>
</div>

<blockquote>📹 Integration demo video — coming soon.</blockquote>

<hr>

<h2>Example prompts to try</h2>
<p>Paste these directly into Cursor, VS Code, or Claude Code after installing a plugin.</p>

<h3>Getting started with an API</h3>
<div class="prompt-example">Set up the Spotify TypeScript SDK and fetch my top 5 tracks. Show me the complete client initialization and the API call.</div>
<div class="prompt-example">How do I authenticate with the Twilio API and send an SMS? Give me the full PHP setup including the SDK client and the send call.</div>
<div class="prompt-example">Walk me through initializing the Slack API client in a Python script and posting a message to a channel.</div>
<div class="prompt-example">How do I get a route between two addresses using the Google Maps Directions API in TypeScript?</div>

<h3>Framework-specific integration</h3>
<div class="prompt-example">I'm building a Next.js app. Integrate the Google Maps Places API to search for nearby restaurants and display them on a page. Use the TypeScript SDK.</div>
<div class="prompt-example">I'm using Laravel. Show me how to send a Twilio SMS when a user registers. Include the PHP SDK setup, client initialization, and the controller code.</div>
<div class="prompt-example">I have an ASP.NET Core app. Add Twilio webhook handling so I can receive delivery status callbacks when an SMS is sent.</div>
<div class="prompt-example">I'm building a Ruby on Rails app. How do I post a Slack message to a channel when a background job finishes?</div>
<div class="prompt-example">I have a Java Spring Boot service. How do I call the Google Maps Geocoding API to convert an address to coordinates?</div>

<h3>Chaining tools for full integrations</h3>
<div class="prompt-example">I want to add real-time order shipping notifications to my Next.js store. Use Twilio to send an SMS when the order status changes to "shipped". Show me the full integration: SDK setup, the correct endpoint and its parameters, and the TypeScript code.</div>
<div class="prompt-example">Build a birthday reminder feature in my Laravel app: look up the correct Twilio endpoint for sending SMS, check the request model, then generate the PHP code that sends a personalized birthday message.</div>
<div class="prompt-example">I need to post a Slack message every time a Spotify track changes in my playlist monitoring app. Walk me through integrating both APIs in TypeScript — start by discovering what's available, then show me the auth setup and the exact API calls.</div>
<div class="prompt-example">In my ASP.NET Core app, I want to geocode user addresses using Google Maps and cache the results. Look up the geocode endpoint and response model, then generate the C# code including error handling.</div>

<h3>Debugging and error handling</h3>
<div class="prompt-example">My Spotify API call is returning 401. What OAuth flow should I be using and how does the TypeScript SDK handle token refresh automatically?</div>
<div class="prompt-example">I'm getting a "21211" error from Twilio when sending SMS. What does this error mean and how do I handle it with the PHP SDK?</div>
<div class="prompt-example">What errors should I handle when calling the Google Maps Directions API in Java, and what do the SDK error types look like?</div>
<div class="prompt-example">My Slack message posts are failing intermittently with rate limit errors. How does the Python SDK expose rate limit information and what's the recommended retry pattern?</div>

<hr>

<h2>Why not just use LLMs.txt or documentation?</h2>
<div class="section-card">
  <div class="why-row"><div class="why-approach">Developer portal</div><div class="why-problem">Developers visit once, then build in their IDE — the gap between the two creates friction</div></div>
  <div class="why-row"><div class="why-approach">LLMs.txt</div><div class="why-problem">Static, machine-readable docs — no SDK-native patterns, no idiomatic code</div></div>
  <div class="why-row"><div class="why-approach">AI without context</div><div class="why-problem">Trained on historical data — confidently generates outdated or incorrect integration code</div></div>
  <div class="why-row highlight"><div class="why-approach">Context Plugin ✓</div><div class="why-problem">SDK-generated, version-aware context delivered where developers actually code</div></div>
</div>

<hr>

<h2>Measured results</h2>
<div class="results-grid">
  <div class="result-item"><div class="result-metric">2×</div><div class="result-desc">faster integration vs. working from documentation alone</div></div>
  <div class="result-item"><div class="result-metric">48%</div><div class="result-desc">lower development cost</div></div>
  <div class="result-item"><div class="result-metric">65%</div><div class="result-desc">reduction in context usage — the AI gets it done with fewer tokens</div></div>
  <div class="result-item"><div class="result-metric">~0</div><div class="result-desc">hallucinations — no fabricated endpoints or non-existent SDK methods</div></div>
</div>
<p style="font-size:14px;">Token efficiency +37%, integration success on complex APIs 83%, code quality ~30% higher, ~70% fewer security issues per thousand lines of code.</p>
<p><a href="https://www.apimatic.io/product/context-plugins/case-study">→ Read the full case study</a></p>

<hr>

<h2>How APIMatic generates a Context Plugin</h2>
<p>APIMatic takes your OpenAPI specification through the same SDK generation pipeline it uses to produce idiomatic, type-safe SDKs in 10+ languages. The resulting MCP server exposes the SDK documentation and integration patterns as structured tool responses that AI assistants can consume natively.</p>
<p>The context the AI receives is:</p>
<ul>
  <li>Derived from actual generated SDK code, not raw documentation</li>
  <li>Inclusive of idiomatic patterns, typed models, and error handling</li>
  <li>Aligned to the current version of your API spec</li>
</ul>
<p style="font-size:14px;">For API providers: <a href="https://www.apimatic.io/request-demo">request a demo</a> to generate a Context Plugin for your own API.</p>

<hr>

<h2>Repository structure</h2>
<div class="repo-block">
  <div><span class="repo-dir">api-context-plugins/</span></div>
  <div>&nbsp;&nbsp;├── <span class="repo-dir">plugins/</span> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="repo-comment"># Per-API plugin configurations and manifests</span></div>
  <div>&nbsp;&nbsp;├── <span class="repo-dir">tools/</span> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="repo-comment"># MCP tool definitions (fetch, ask, search-endpoint, search)</span></div>
  <div>&nbsp;&nbsp;├── <span class="repo-dir">docs/</span> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span class="repo-comment"># Implementation guides and integration references</span></div>
  <div>&nbsp;&nbsp;└── <span class="repo-dir">examples/</span> &nbsp;&nbsp;&nbsp;<span class="repo-comment"># Sample apps and usage walkthroughs per API</span></div>
</div>

<hr>

<h2>Contributing</h2>
<p>Found an issue with a specific plugin or want to request an API? <a href="../../issues">Open an issue</a> or reach out at <a href="mailto:support@apimatic.io">support@apimatic.io</a>.</p>

<hr>

<h2>Learn more</h2>
<div class="link-list">
  <a class="link-pill" href="https://www.apimatic.io/product/context-plugins">Product page</a>
  <a class="link-pill" href="https://www.apimatic.io/blog/from-api-portals-to-cursor">Blog: From API Portals to Cursor</a>
  <a class="link-pill" href="https://docs.apimatic.io/">APIMatic docs</a>
  <a class="link-pill" href="https://www.apimatic.io/free-trial">Free trial</a>
</div>

</body>
</html>
