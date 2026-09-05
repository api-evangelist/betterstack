---
name: betterstack-triage-and-resolve-incident
description: Find open Better Stack incidents, read the timeline, acknowledge, escalate if needed, and resolve — with the 24-hour reopen window as the only undo.
api: Better Stack Incidents API
base_url: https://uptime.betterstack.com/api/v2
operations:
  - listIncidents
  - getIncident
  - getIncidentTimeline
  - acknowledgeIncident
  - escalateIncident
  - resolveIncident
  - reopenIncident
generated: '2026-09-04'
method: generated
source: >-
  Grounded in the operationIds in openapi/betterstack-incidents-api-openapi.yml, the
  reversibility analysis in conventions/betterstack-conventions.yml, and Better Stack's own MCP
  tool reference (https://betterstack.com/docs/getting-started/integrations/mcp/), which is
  where the 24-hour reopen window is stated.
---

# Triage and resolve an incident

## Consequences before you act

This is the most consequential surface Better Stack exposes. Read this before calling anything:

- **`escalateIncident` pages a human.** It routes the incident to a user, team, schedule or
  policy, and the notification leaves immediately. There is **no de-escalate operation**. Never
  escalate speculatively, and never escalate as a way of "getting attention" on an incident an
  agent could resolve.
- **`acknowledgeIncident` cannot be undone.** Acknowledging stops escalation. There is no
  un-acknowledge operation. If you acknowledge an incident nobody is actually working, you have
  silently suppressed the page.
- **`resolveIncident` CAN be undone — for 24 hours.** `reopenIncident` reopens a resolved
  incident within 24 hours of resolution. After that window the resolution is final. This is the
  only reversal window Better Stack states anywhere.
- **`deleteIncident` is permanent** and destroys the timeline. Do not call it as part of triage.

## Steps

1. **List what is open.** Call `listIncidents` (`GET /incidents`). Filter to the incidents you
   care about and paginate with `page` / `per_page` (default 50, max 250) until
   `pagination.next` is null.

2. **Read one incident.** Call `getIncident` (`GET /incidents/{id}`) for the full record.

3. **Read the history before deciding.** Call `getIncidentTimeline`
   (`GET /incidents/{id}/timeline`). The timeline shows what has already happened — including
   whether someone has already acknowledged or escalated. Skipping this is how an agent
   double-pages an on-call engineer.

4. **Acknowledge only if you or a named human is taking ownership.** Call
   `acknowledgeIncident` (`POST /incidents/{id}/acknowledge`). This stops escalation, so only
   do it when the incident is genuinely being worked.

5. **Escalate only on explicit human instruction.** Call `escalateIncident`
   (`POST /incidents/{id}/escalate`). Confirm the target with the requester first. This step
   should never be taken autonomously.

6. **Resolve when the underlying problem is fixed.** Call `resolveIncident`
   (`POST /incidents/{id}/resolve`).

7. **If you resolved wrongly, reopen within 24 hours.** Call `reopenIncident`
   (`POST /incidents/{id}/reopen`). Past 24 hours this will not work and you must open a new
   incident instead.

## Error handling

- `401` — `{"errors": "Invalid Team API token..."}`; the token is missing, wrong, or scoped to
  the wrong team.
- `404` — `{"errors": "Endpoint ... does not exist.", "see_docs": "..."}`.
- The state transitions (acknowledge / resolve / reopen) are state assignments, so re-sending
  one is safe. **`createIncident` is not** — there is no idempotency key, and a retry creates a
  duplicate incident that will page again.
- Both `/api/v2/incidents` and `/api/v3/incidents` answer live. Better Stack publishes no
  versioning policy saying which is current; use the version your account's docs show and do
  not switch mid-workflow.
