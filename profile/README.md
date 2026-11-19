# Skunky — Skunkworks automation platform

**Skunky** is the platform organization for Skunkworks' modular search, extraction, data normalization, and workflow automation products. **SkunkScrape** is the existing lead discovery product being integrated into this architecture, not a separate competing platform.

## Architecture

```text
Public Web UI (www)   Operator Console (studio)   Conversational UI (chat)
                 \          |          /
                       API (control plane)
                         |
                  Search (source discovery)
                         |
                 Scan (HTML extraction)
                         |
                 Collect (normalization)
                         |
       Sources registry / approved integrations
```

The initial implementation uses **explicit, bounded, caller-supplied HTML** for extraction; live crawling requires an independently reviewed fetcher with robots/ToS, SSRF defense, approved egress, and privacy controls. The control plane must not report synthetic leads as real extraction results.

| Repository | Responsibility |
|---|---|
| [www](https://github.com/skunky-bot/www) | Public application, existing Next.js frontend; legacy SkunkScrape Python engine preserved |
| [api](https://github.com/skunky-bot/api) | Authenticated API/control plane, orchestration, job contracts |
| [search](https://github.com/skunky-bot/search) | Discovery and allowlisted source search |
| [scan](https://github.com/skunky-bot/scan) | Bounded HTML parsing and extraction, not unrestricted crawling |
| [collect](https://github.com/skunky-bot/collect) | Deduplication and normalization, with provenance |
| [chat](https://github.com/skunky-bot/chat) | Conversational client; no secrets or model access in browser |
| [studio](https://github.com/skunky-bot/studio) | Operator/developer console, existing Python toolkit preserved |
| [sources](https://github.com/skunky-bot/sources) | Source registry, permissions, provenance |
| [skunkscrape-integrations](https://github.com/skunky-bot/skunkscrape-integrations) | Explicit opt-in CRM and webhook adapters |
| [.github](https://github.com/skunky-bot/.github) | Organization profile, templates, policies |

Legacy experiments such as SkunkScrapeCodex are **reference implementations** until a reviewed ADR decides their migration or deprecation.

## Governance

- All production-impacting changes via protected PR, CI, secret scanning and appropriate approval.
- No credentials or personal lead data in Git; use scoped managed secrets and audited retention.
- POPIA, DNC, opt-out, purpose limits and source rights are **release gates**, not just documentation.
- Service-to-service communication is authenticated; do not expose internal services publicly without a gateway.
- The platform architecture and implementation status are documented in [www/docs/architecture](https://github.com/skunky-bot/www/tree/main/docs/architecture).

Skunkworks (Pty) Ltd · https://www.skunkworks.africa
