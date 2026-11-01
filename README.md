# tZERO

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

tZERO Technologies is a US financial-technology company building regulated infrastructure for tokenized real-world assets and digital securities. Through its SEC- and FINRA-regulated broker-dealer, Alternative Trading System (tZERO ATS, continuously operating since 2019), special purpose broker-dealer for digital custody, and SEC-registered transfer agent, tZERO covers the full lifecycle: capital formation and token issuance, secondary trading and market data, clearance and settlement, cap-table recordkeeping, corporate actions, dividends and proxy voting. Its developer surface — marketed as tZERO Connect — publishes two public OpenAPI 3.0.3 contracts (an Issuance & Secondary Markets REST API on gateway-web-api.tzero.com and an Institutional transfer-agent / tokenization / custody API on api.t0direct.com) alongside FIX 4.2 / 4.4 specifications for order entry, drop copy and market data.

**Areas:** Company · Digital Securities · Tokenization · Capital Markets · Trading · Alternative Trading System · Transfer Agent · Custody · Blockchain · Financial Services · Securities · Market Data

## tZERO on APIs.io

Everything profiled for tZERO is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/tzero/](https://apis.io/providers/tzero/)** — or go straight to one of the APIs or properties below.

### APIs (29)

- [tZERO FIX API](https://apis.io/apis/tzero/fix/) — FIX 4.2 / 4.4 protocol surface for low-latency order entry, drop-copy execution reports, market data (snapshot and incremental refresh, trading session…
- [tZERO Authorization API](https://apis.io/apis/tzero/tzero-authorization-api/) — The Authorization API from tZERO — 2 operation(s) for authorization.
- [tZERO Balance API](https://apis.io/apis/tzero/tzero-balance-api/) — Retrieving fiat balances and asset position balances for an account.
- [tZERO Bank Accounts API](https://apis.io/apis/tzero/tzero-bank-accounts-api/) — Managing bank accounts linked to an investor account (add, list, delete, verify).
- [tZERO Corporate Actions API](https://apis.io/apis/tzero/tzero-corporate-actions-api/) — Splits, mergers and other corporate actions — review-gated; on-chain splits broadcast via Fireblocks
- [tZERO Custody Accounts API](https://apis.io/apis/tzero/tzero-custody-accounts-api/) — The Custody Accounts API from tZERO — 12 operation(s) for custody accounts.
- [tZERO Custody Assets API](https://apis.io/apis/tzero/tzero-custody-assets-api/) — Supported assets, address validation, and fee estimation (live)
- [tZERO Custody Transfers API](https://apis.io/apis/tzero/tzero-custody-transfers-api/) — Transfers of assets out of custody vaults
- [tZERO Deployments API](https://apis.io/apis/tzero/tzero-deployments-api/) — On-chain instances of tokens and their operation history
- [tZERO Dividends API](https://apis.io/apis/tzero/tzero-dividends-api/) — Dividend declarations (cash & stock) — review-gated; on-chain execution via the dividend claim contract
- [tZERO Documents API](https://apis.io/apis/tzero/tzero-documents-api/) — Investor document upload and retrieval
- [tZERO Investments API](https://apis.io/apis/tzero/tzero-investments-api/) — Investments and assets (create, update, submit, cancel, agreements).
- [tZERO Investor Accounts API](https://apis.io/apis/tzero/tzero-investoraccounts-api/) — The InvestorAccounts API from tZERO — 2 operation(s) for investoraccounts.
- [tZERO Investors API](https://apis.io/apis/tzero/tzero-investors-api/) — Investor KYC, accreditation, and holdings management
- [tZERO Iso API](https://apis.io/apis/tzero/tzero-iso-api/) — The Iso API from tZERO — 4 operation(s) for iso.
- [tZERO Issuances API](https://apis.io/apis/tzero/tzero-issuances-api/) — Primary share issuance requests
- [tZERO Markets API](https://apis.io/apis/tzero/tzero-markets-api/) — Market schedule information including pre-market, regular, and post-market hours.
- [tZERO Onboarding API](https://apis.io/apis/tzero/tzero-onboarding-api/) — Managing accounts and users (create account, KYC, trusted contact, financial info).
- [tZERO Proposals API](https://apis.io/apis/tzero/tzero-proposals-api/) — Shareholder voting — proposal creation and results; off-chain or on-chain (anchored) voting modes
- [tZERO Securities API](https://apis.io/apis/tzero/tzero-securities-api/) — Security and instrument definitions
- [tZERO Settlements API](https://apis.io/apis/tzero/tzero-settlements-api/) — The Settlements API from tZERO — 8 operation(s) for settlements.
- [tZERO Subred API](https://apis.io/apis/tzero/tzero-subred-api/) — The Subred API from tZERO — 1 operation(s) for subred.
- [tZERO SubRed Embed API](https://apis.io/apis/tzero/tzero-subred-embed-api/) — The SubRed Embed API from tZERO — 8 operation(s) for subred embed.
- [tZERO Tokens API](https://apis.io/apis/tzero/tzero-tokens-api/) — Token configurations — the issuer's token blueprints
- [tZERO Trading API](https://apis.io/apis/tzero/tzero-trading-api/) — Order management for secondary-market trading (fees, submit, cancel, list orders).
- [tZERO Transfers API](https://apis.io/apis/tzero/tzero-transfers-api/) — Book-entry transfer requests (secondary)
- [tZERO Vaults API](https://apis.io/apis/tzero/tzero-vaults-api/) — Custody vaults and their asset wallets
- [tZERO Webhooks API](https://apis.io/apis/tzero/tzero-webhooks-api/) — Webhook subscription management and event delivery
- [tZERO Whitelist API](https://apis.io/apis/tzero/tzero-whitelist-api/) — Approved external addresses for custody transfers

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Tzero Institutional Webhooks](https://apis.io/asyncapis/tzero/tzero-institutional-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [tzero](https://apis.io/servers/tzero/tzero/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Tzero Agentic Access](https://apis.io/agentic-access/tzero/tzero-agentic-access/)

#### Overlays (2)

OpenAPI overlays, including conversational phrasing for each operation.

- [Tzero Institutional Overlay](https://apis.io/overlays/tzero/tzero-institutional-overlay/)
- [Tzero Issuance Secondary Markets Overlay](https://apis.io/overlays/tzero/tzero-issuance-secondary-markets-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Tzero Authentication](https://apis.io/security/tzero/tzero-authentication/)
- [Tzero Domain Security](https://apis.io/security/tzero/tzero-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Tzero Plans Pricing](https://apis.io/plans/tzero/tzero-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Tzero Rate Limits](https://apis.io/rate-limits/tzero/tzero-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://www.tzero.com/)
- [Documentation](https://apidocs.tzero.com/docs)
- [Getting started](https://apidocs.tzero.com/docs)
- [API reference](https://apidocs.tzero.com/docs/explorer)
- [Sign up](https://platform.tzero.com/tzero/register)
- [Support](https://www.tzero.com/contact)
- [Blog](https://www.tzero.com/content-hub)
- [Compliance](https://www.tzero.com/legal)
- [Terms of service](https://storage.googleapis.com/public-disclosures.tzero.com/tZERO_MasterTermsofUse.pdf)
- [Privacy policy](https://storage.googleapis.com/public-disclosures.tzero.com/Privacy-Policy-and-Privacy-Notices-(TDAS-and-tZERO-Securities).pdf)
- [GitHub](https://github.com/tZERO-dev)

## API Evangelist rating

**Kin Score 47.6** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 57.1 |
| Contract quality | 55.9 |
| Contract governance | 18.2 |
| Operational transparency | 26.3 |
| Developer ergonomics | 58.9 |
| Access clarity | 35.5 |

**Agent readiness 45.7** — agent-native

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | verified |
| Error Semantics | verified |
| OpenAPI Examples | partial |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 33.3** — Securities & Market Data

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/tzero/](https://apis.io/providers/tzero/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for tZERO: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/tzero/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
