# Deploy and Host Open Notebook on Railway

Open Notebook is a privacy-focused, open-source research workspace for organizing sources, chatting with AI over your content, and generating multi-speaker podcasts.

## About Hosting Open Notebook

This template deploys Open Notebook `1.14.0`, SurrealDB `2.6.5`, and a Caddy `2.11.4` proxy. The proxy is the only public application entry point and routes the web interface and API through one HTTPS origin. Open Notebook connects to SurrealDB over Railway private networking.

The application volume persists local Open Notebook data at `/app/data`, while SurrealDB stores its database on a separate volume at `/data`.

## Common Use Cases

- Organize PDFs, videos, web pages, and notes into research notebooks
- Ask grounded questions using your own source collection
- Generate multi-speaker podcast episodes from notebook content
- Operate a private, self-hosted AI knowledge workspace

## Dependencies for Open Notebook Hosting

- An API key for at least one supported AI provider
- Open Notebook `1.14.0`
- SurrealDB `2.6.5`
- Caddy `2.11.4`
- Two persistent Railway volumes

### Deployment Dependencies

- [Open Notebook documentation](https://www.open-notebook.ai)
- [Open Notebook source](https://github.com/lfnovo/open-notebook)
- [SurrealDB documentation](https://surrealdb.com/docs)
- [Proxy source](https://github.com/monotykamary/railway-open-notebook-caddy-proxy)

### Implementation Details

Open the generated `proxy` domain after deployment. The template wires `API_URL` to that public origin and keeps the Open Notebook web and API ports private. SurrealDB credentials are generated independently and passed to Open Notebook with Railway service references.

Configure `OPENAI_API_KEY` during deployment, or replace it afterward with credentials for another supported provider. After validating the application, optionally set `OPEN_NOTEBOOK_PASSWORD` on the `open-notebook` service and redeploy to require a password.

Do not remove either persistent volume when updating the stack. Database credentials are generated per deployment and are not stored in this overview.

## Why Deploy Open Notebook on Railway?

Railway provides private service networking, HTTPS, persistent volumes, generated secrets, health checks, and centralized logs. The template exposes one browser origin while keeping its application ports and database connection private.
