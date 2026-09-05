---
name: betterstack-cover-a-cron-job-with-a-heartbeat
description: Create a Better Stack heartbeat so a scheduled job pages someone when it stops running, then confirm it is receiving pings.
api: Better Stack Heartbeats API
base_url: https://uptime.betterstack.com/api/v2
operations:
  - listHeartbeats
  - createHeartbeat
  - getHeartbeat
  - getHeartbeatAvailability
  - updateHeartbeat
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the operationIds and the HeartbeatCreate schema in
  openapi/betterstack-heartbeats-api-openapi.yml, plus
  conventions/betterstack-conventions.yml.
---

# Cover a scheduled job with a heartbeat

A heartbeat is an inverted monitor: your job pings Better Stack, and Better Stack raises an
incident when the ping does **not** arrive.

## Before you start

- `Authorization: Bearer $TOKEN` with an Uptime or Global API token.
- Base URL `https://uptime.betterstack.com/api/v2`.
- No idempotency key exists. Pre-check before creating.
- `deleteHeartbeat` is permanent with no restore path.

## Steps

1. **Check it does not already exist.** Call `listHeartbeats` (`GET /heartbeats`) and page
   through with `page` / `per_page` until `pagination.next` is null.

2. **Create the heartbeat.** Call `createHeartbeat` (`POST /heartbeats`). The two fields that
   decide whether this works are:
   - `name` (required) — name it after the job, not the server.
   - `period` (required, seconds) — the expected interval between pings.
   - `grace` (seconds) — slack before an incident is raised. Set this from the job's real
     worst-case runtime, not its average, or the heartbeat will page on a slow night.
   - `policy_id` — the escalation policy to page. Without it the alert may go nowhere useful.
   - `call`, `sms`, `email`, `push` — notification channels.
   - `team_wait` (seconds) — delay before the wider team is notified.
   - `paused` — create it paused if the job is not live yet.

3. **Record the id and wire the ping.** Take `data.id` from the response and configure the job
   to ping Better Stack on every successful run.

4. **Confirm.** Call `getHeartbeat` (`GET /heartbeats/{id}`) to check the configuration, then,
   after at least one `period` has elapsed, call `getHeartbeatAvailability`
   (`GET /heartbeats/{id}/availability`) to confirm pings are arriving.

5. **Tune rather than recreate.** If the grace period is wrong, call `updateHeartbeat`
   (`PATCH /heartbeats/{id}`). Do not delete and recreate — you lose the history.

## Error handling

- `401` / `404` return `{"errors": "<string>"}`; there is no machine-readable error code.
- A timed-out `createHeartbeat` may have succeeded. Re-run step 1 before retrying.
