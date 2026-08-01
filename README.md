# Cardless

Cardless, Inc. is a San Francisco fintech operating an embedded co-branded credit card platform. Consumer brands use Cardless APIs and pre-built components to launch and run their own credit card programs natively inside their apps and websites, while Cardless handles issuing-bank relationships, card production, underwriting, fraud, KYC/AML compliance, servicing and support. The platform is network-agnostic across Visa, Mastercard and American Express.

Named partners include Coinbase (Coinbase One Card), Bilt, Qatar Airways Privilege Club, Alibaba.com, LATAM Airlines, Avianca LifeMiles, TAP Air Portugal and Avelo Airlines.

- Website: https://www.cardless.com/
- Platform: https://www.cardless.com/platform
- Documentation: https://docs.cardless.com/ (partner login required)
- Blog: https://www.cardless.com/blog
- Secondary-market listing (harvest source): https://forgeglobal.com/cardless_stock/

## Access model

Cardless is a **partner-onboarded** platform. There is no public sign-up for API credentials and no public developer surface:

- `docs.cardless.com` redirects every page to `/login`; its sitemap is empty.
- `api.cardless.com` is live and answers every unauthenticated request with `401 {"message":"Unauthorized"}`.
- No public OpenAPI, AsyncAPI, webhook catalog, SDK, CLI, Postman collection, sandbox credentials, security.txt, trust center, public status page or A2A Agent Card was found.

## What is published

| Artifact | What it captures |
|---|---|
| `mcp/` | The **Cardless Docs MCP server** at `https://docs.cardless.com/mcp` — a Mintlify-hosted MCP that answers `tools/list` anonymously with three tools, plus its verbatim tools/list response |
| `well-known/` | RFC 8414 authorization-server and RFC 9728 protected-resource metadata (both 200), and the full negative probe index across every Cardless host |
| `scopes/` | The single `mcp:search` scope published by the docs MCP authorization server |
| `authentication/` | Partner Basic-auth → bearer-token exchange (account-scoped, JWT), plus the docs MCP OAuth model |
| `conventions/` | Identifiers, error envelope, production vs staging estate, versioning findings |
| `conformance/` | OAuth 2.0, RFC 8414, RFC 9728, PKCE, DCR, JWT, MCP 2025-06-18 — and the honest negatives |
| `lifecycle/` | Versioning, deprecation, status page and changelog findings (all absent or gated) |
| `components/` | The publicly described embeddable component surface (application flow, checkout, card management, disputes, rewards) |
| `security/` | TLS/HSTS/DNSSEC/CAA/SPF/DMARC probe results |
| `llms/` | Generated `llms.txt` for this provider |

## Note on the gated documentation

The Cardless documentation corpus is deliberately gated behind a partner login, but the MCP endpoint on the same host answers anonymously and its read-only filesystem tool exposes the gated corpus, including the OpenAPI fragments that back the API reference. API Evangelist recorded the **existence and shape** of that contract as catalog metadata and deliberately did **not** copy the gated specification or documentation bodies into this public repository. The finding is documented in `mcp/cardless-mcp.yml` under `x-observation`.
