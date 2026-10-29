# Better Stack

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

Better Stack is an infrastructure monitoring and observability platform that combines uptime monitoring, heartbeat monitoring for scheduled jobs, incident management with on-call paging and escalation policies, public and private status pages, log/trace/metric telemetry queried with ClickHouse SQL, error tracking with session replay, and an AI SRE for automated root cause analysis. It is OpenTelemetry-native on ingestion — OTLP/HTTP endpoints for logs, traces and metrics — and publishes three REST management surfaces (Uptime v2, Telemetry v1, Errors v1) declared in its own RFC 9727 /.well-known/api-catalog, alongside a first-party remote MCP server at mcp.betterstack.com exposing roughly 106 agent tools behind OAuth 2.1.

**Areas:** Observability · Uptime Monitoring · Incidents · Logs · Monitoring · Status Pages · On-Call · Error Tracking · OpenTelemetry · MCP

## Better Stack on APIs.io

Everything profiled for Better Stack is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/betterstack/](https://apis.io/providers/betterstack/)** — or go straight to one of the APIs or properties below.

### APIs (6)

- [Better Stack Heartbeats API](https://apis.io/apis/betterstack/betterstack-heartbeats-api/) — The Heartbeats API from Better Stack — create and manage heartbeat monitors that alert when a cron job or background task stops reporting.
- [Better Stack Incidents API](https://apis.io/apis/betterstack/betterstack-incidents-api/) — The Incidents API from Better Stack — create, acknowledge, escalate, resolve and reopen incidents, and read the incident timeline.
- [Better Stack Monitors API](https://apis.io/apis/betterstack/betterstack-monitors-api/) — The Monitors API from Better Stack — create and manage uptime monitors and read their availability and response-time series.
- [Better Stack Status Pages API](https://apis.io/apis/betterstack/betterstack-status-pages-api/) — The Status Pages API from Better Stack — create and manage public and private status pages and the resources shown on them.
- [Better Stack Telemetry API](https://apis.io/apis/betterstack/betterstack-telemetry-api/) — The Telemetry API from Better Stack — manage log, trace and metric sources, fields, metric expressions, dashboards, charts and chart alerts. Declared by…
- [Better Stack Errors API](https://apis.io/apis/betterstack/betterstack-errors-api/) — The Errors API from Better Stack — manage error-tracking applications, application groups and releases, and triage error patterns and exceptions. Declared…

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Betterstack Webhooks](https://apis.io/asyncapis/betterstack/betterstack-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [Better Stack MCP Server](https://apis.io/servers/betterstack/better-stack-mcp-server/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Betterstack Agentic Access](https://apis.io/agentic-access/betterstack/betterstack-agentic-access/)

#### Collections (5)

Postman and Open Collection request collections.

- [Better Stack Uptime API](https://apis.io/collections/betterstack/open-betterstack/)
- [Better Stack Uptime Heartbeats API](https://apis.io/collections/betterstack/open-betterstack-heartbeats-api/)
- [Better Stack Uptime Heartbeats Incidents API](https://apis.io/collections/betterstack/open-betterstack-incidents-api/)
- [Better Stack Uptime Heartbeats Monitors API](https://apis.io/collections/betterstack/open-betterstack-monitors-api/)
- [Better Stack Uptime Heartbeats Status Pages API](https://apis.io/collections/betterstack/open-betterstack-status-pages-api/)

#### Overlays (8)

OpenAPI overlays, including conversational phrasing for each operation.

- [Betterstack Heartbeats Api Phrasing Overlay](https://apis.io/overlays/betterstack/betterstack-heartbeats-api-phrasing-overlay/)
- [Betterstack Heartbeats Overlay](https://apis.io/overlays/betterstack/betterstack-heartbeats-overlay/)
- [Betterstack Incidents Api Phrasing Overlay](https://apis.io/overlays/betterstack/betterstack-incidents-api-phrasing-overlay/)
- [Betterstack Incidents Overlay](https://apis.io/overlays/betterstack/betterstack-incidents-overlay/)
- [Betterstack Monitors Api Phrasing Overlay](https://apis.io/overlays/betterstack/betterstack-monitors-api-phrasing-overlay/)
- [Betterstack Monitors Overlay](https://apis.io/overlays/betterstack/betterstack-monitors-overlay/)
- [Betterstack Status Pages Api Phrasing Overlay](https://apis.io/overlays/betterstack/betterstack-status-pages-api-phrasing-overlay/)
- [Betterstack Status Pages Overlay](https://apis.io/overlays/betterstack/betterstack-status-pages-overlay/)

#### Security (4)

Authentication, trust centre, and vulnerability disclosure.

- [Betterstack Authentication](https://apis.io/security/betterstack/betterstack-authentication/)
- [Betterstack Domain Security](https://apis.io/security/betterstack/betterstack-domain-security/)
- [Betterstack Trust Center](https://apis.io/security/betterstack/betterstack-trust-center/)
- [Betterstack Vulnerability Disclosure](https://apis.io/security/betterstack/betterstack-vulnerability-disclosure/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Betterstack Scopes](https://apis.io/scopes/betterstack/betterstack-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Betterstack Plans Pricing](https://apis.io/plans/betterstack/betterstack-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Betterstack Rate Limits](https://apis.io/rate-limits/betterstack/betterstack-rate-limits/)

#### FinOps (1)

What the API costs to run, by operation.

- [Betterstack Finops](https://apis.io/finops/betterstack/betterstack-finops/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://betterstack.com/)
- [Documentation](https://betterstack.com/docs/)
- [Getting started](https://betterstack.com/docs/uptime/api/getting-started-with-uptime-api/)
- [API reference](https://betterstack.com/docs/uptime/api)
- [Pricing](https://betterstack.com/pricing)
- [Sign up](https://betterstack.com/users/sign-up)
- [Support](https://betterstack.com/help)
- [Changelog](https://betterstack.com/tag/changelog)
- [Blog](https://betterstack.com/community/blog)
- [Terms of service](https://betterstack.com/terms)
- [Privacy policy](https://betterstack.com/privacy)
- [GitHub](https://github.com/BetterStackHQ)
- [Status](https://status.betterstack.com/)

## API Evangelist rating

**Kin Score 67.0** — exemplar · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 75.0 |
| Contract quality | 56.6 |
| Contract governance | 31.8 |
| Operational transparency | 44.7 |
| Developer ergonomics | 67.3 |
| Access clarity | 92.1 |

**Agent readiness 58.0** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | verified |
| Auth Clarity | served (partial credit) |
| Idempotency | — |
| Error Semantics | documented (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | yes |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | served (partial credit) |
| Protected Resource Metadata | verified |
| Dynamic Client Registration | yes |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 45.1** — Horizontal (data, software, accessibility, platform)

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/betterstack/](https://apis.io/providers/betterstack/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Better Stack: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/betterstack/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
