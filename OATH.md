# OATH / OAuth Configuration

## Status

All external vendor OAuth flows **MUST** route through BlackRoad OS infrastructure (Cloudflare + Tailscale mesh). No vendor token or credential exchange may bypass the self-hosted gateway.

## Architecture

```
Client → Cloudflare Pages (edge) → Cloudflare Access (OATH gate) → Tailscale mesh → BlackRoad Pi cluster
```

## Cloudflare Access (OATH)

OAuth is handled via **Cloudflare Access** — zero-trust, no third-party OAuth provider required:

1. Log in to [Cloudflare Zero Trust dashboard](https://one.dash.cloudflare.com/)
2. **Access → Applications → Add an Application**
3. Select **Self-hosted**
4. Set the application domain to your Pages domain (e.g. `blackroad-brand-official.pages.dev` or your custom domain)
5. Set identity providers to your preferred provider (GitHub, Google, or a self-hosted IdP via Cloudflare Access)
6. Enforce **Require Authentication** for all paths that need protection

This eliminates the need for OpenAI / Anthropic / GitHub Copilot OAuth tokens flowing through any third-party relay.

## Tailscale Integration

To ensure all AI vendor API calls route through your Tailscale mesh:

1. Install Tailscale on your Pi cluster nodes
2. Configure a Tailscale exit node or subnet router on one Pi
3. Point any local agent (e.g. @blackboxprogramming tooling) at the Tailscale subnet router as the API gateway
4. Use Cloudflare Tunnel (`cloudflared`) to expose only the services you choose — nothing else is reachable from the public internet

```
You ──► Cloudflare Tunnel ──► Tailscale subnet router (Pi) ──► BlackRoad services
```

## Custom API Vendor Routing

All vendor API calls must be proxied through the BlackRoad gateway. Set the following environment variables in your client tools to override vendor base URLs:

| Vendor | Env Var | Value |
|--------|---------|-------|
| OpenAI | `OPENAI_API_BASE` | `https://api.blackroad.io/v1/openai` |
| Anthropic | `ANTHROPIC_BASE_URL` | `https://api.blackroad.io/v1/anthropic` |
| GitHub | `GITHUB_API_URL` | `https://api.blackroad.io/v1/github` |
| Generic | `AI_GATEWAY_URL` | `https://api.blackroad.io/v1` |

The Cloudflare AI Gateway (see `wrangler.toml`) handles routing and caching at the edge.

## Approved AI Systems

Only the following AI systems are authorized to interact with this repository:

- **@blackboxprogramming** (primary)
- **@lucidia** (primary)

All other AI agents (Copilot, Codex, Claude, ChatGPT, etc.) are **not authorized** to commit, review, or merge changes.

---

© 2026 BlackRoad OS, Inc. — Proprietary
