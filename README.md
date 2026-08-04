# Cardless

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
