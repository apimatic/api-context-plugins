# API Context Plugins

General-purpose AI models are trained on public code and documentation, much of it outdated. They have no awareness of an actual API version, latest SDKs or the recommended workflows.

API Context Plugins give coding assistants deterministic, version-aware API context, generated directly from your API definition and SDKs. Instead of scraping public documentation or guessing from memory, the AI is grounded in the exact OpenAPI definition, current SDK versions, executable, idiomatic code samples, and recommended integration workflows.
  
## MCP Server

- `api-context-plugins` — Get integration and implementaiton knowledge for third-party APIs

## Skills

- **integrate-api-context-plugins** — Guidance for discovering and integrating third-party APIs using the api-context-plugins MCP server
- **onboard-api-context-plugins** — Interactive onboarding tour: explains the MCP, lists available APIs, lets the user pick one to explore, demonstrates model_search and endpoint_search live, and provides a menu of suggested actions