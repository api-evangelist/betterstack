---
name: betterstack-provision-uptime-monitor
description: Create an uptime monitor for a new service in Better Stack, confirm it was created, and verify it is reporting.
api: Better Stack Monitors API
base_url: https://uptime.betterstack.com/api/v2
operations:
  - createMonitor
  - getMonitor
  - listMonitors
  - getMonitorAvailability
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the operationIds in openapi/betterstack-monitors-api-openapi.yml and the
  conventions recorded in conventions/betterstack-conventions.yml. Note that the OpenAPI is an
  API Evangelist reconstruction from Better Stack's public docs, not a provider-published
  contract — verify request bodies against https://betterstack.com/docs/uptime/api/monitors/
  before running against a production account.
---

# Provision an uptime monitor

## Before you start

- Get an **Uptime API token** (team-scoped) or a **Global API token** from
  Better Stack → API tokens. Send it as `Authorization: Bearer $TOKEN`.
- Base URL is `https://uptime.betterstack.com/api/v2`. Responses are JSON;
  Better Stack describes them as JSON:API.
- **There is no idempotency key.** A retried `createMonitor` creates a SECOND monitor.
  If the call times out or the connection drops, do NOT retry blindly — run step 3 first.
- **Deletion is permanent.** `deleteMonitor` has no restore path and takes the monitor's
  availability history with it. Never call it to clean up after a failed create; find the
  duplicate and delete only the one you just made, after confirming its id.

## Steps

1. **Check for an existing monitor first.** Call `listMonitors`
   (`GET /monitors?per_page=250`) and look for the URL you are about to add. Because there is
   no idempotency key, this pre-check is the only duplicate protection available.
   Paginate with `page` and `per_page` (default 50, max 250) until `pagination.next` is null.

2. **Create the monitor.** Call `createMonitor` (`POST /monitors`) with the target URL and the
   check parameters the caller asked for. Record the returned `data.id` immediately —
   it is an opaque string with no type prefix, so note that it is a MONITOR id.

3. **If step 2 did not return cleanly**, do not retry. Call `listMonitors` again and search for
   the URL. If it is there, the write succeeded and only the response was lost.

4. **Confirm the monitor.** Call `getMonitor` (`GET /monitors/{id}`) with the id from step 2 and
   check the configuration matches what was requested.

5. **Verify it is reporting.** After the first check interval has elapsed, call
   `getMonitorAvailability` (`GET /monitors/{id}/availability`) to confirm Better Stack is
   actually collecting data for it.

## Error handling

- `401` — body is `{"errors": "Invalid Team API token..."}`. The same response is returned for
  a missing token and a wrong token, so re-check that the header was sent at all before
  reissuing the credential. An Uptime resource needs an Uptime or Global token, not a
  Telemetry token.
- `404` — body is `{"errors": "Endpoint ... does not exist.", "see_docs": "..."}`. Routing 404s
  are returned before auth is evaluated; check the method and path.
- The `errors` member is a human-readable **string**, not an array and not RFC 9457 problem
  details. There is no machine-readable error code — do not branch on one.
- Better Stack publishes no rate limits and returns no `RateLimit-*` or `Retry-After` headers.
  Back off conservatively on repeated failures; you have no published budget to reason about.
