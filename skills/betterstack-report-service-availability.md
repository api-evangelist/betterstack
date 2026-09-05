---
name: betterstack-report-service-availability
description: Pull availability and response-time data for Better Stack monitors and turn it into an SLA report, read-only.
api: Better Stack Monitors API
base_url: https://uptime.betterstack.com/api/v2
operations:
  - listMonitors
  - getMonitor
  - getMonitorAvailability
  - getMonitorResponseTimes
  - listHeartbeats
  - getHeartbeatAvailability
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the operationIds in openapi/betterstack-monitors-api-openapi.yml and
  openapi/betterstack-heartbeats-api-openapi.yml, plus
  conventions/betterstack-conventions.yml.
---

# Report service availability

This flow is **entirely read-only**. It calls no write operation, so idempotency and
reversibility do not apply — a safe skill to run autonomously.

## Steps

1. **Enumerate monitors.** Call `listMonitors` (`GET /monitors`). Page with
   `?per_page=250&page=N` and stop when `pagination.next` is null. Do not assume one page:
   the default is 50.

2. **Enumerate heartbeats too** if scheduled jobs are in scope. Call `listHeartbeats`
   (`GET /heartbeats`) with the same pagination.

3. **Pull availability per monitor.** For each id, call `getMonitorAvailability`
   (`GET /monitors/{id}/availability`). This is the SLA summary — uptime percentage over the
   period.

4. **Pull response times where latency matters.** Call `getMonitorResponseTimes`
   (`GET /monitors/{id}/response-times`) for the performance series.

5. **Pull heartbeat availability.** `getHeartbeatAvailability`
   (`GET /heartbeats/{id}/availability`) for each heartbeat id.

6. **Attribute correctly.** Ids are opaque strings with no type prefix — a monitor id and a
   heartbeat id look identical. Keep them in separate collections; do not merge the two id
   spaces into one map.

## Pacing

Better Stack publishes no rate limits and emits no `RateLimit-*` or `Retry-After` headers, so
there is no budget to read. Step 3 issues one request per monitor: on a large account, pace the
loop and stop on the first sustained failure rather than hammering an undocumented limit.

## Error handling

- `401` — `{"errors": "Invalid Team API token..."}`.
- `404` — `{"errors": "...", "see_docs": "..."}`; check the id came from the right collection.
