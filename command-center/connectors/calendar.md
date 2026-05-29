# Connector: Google Calendar

Native connector tools: `mcp__claude_ai_Google_Calendar__*`. Read-only in v1 — used by the morning brief.

## Inputs
| Source | Tool | Scope | Why |
|---|---|---|---|
| Today's events | `list_events` | timeMin = today 00:00, timeMax = today 23:59, my primary calendar | The day's schedule for the brief |
| Event detail | `get_event` | A single event | Only if I ask about a specific meeting |

## Process
1. `list_events` for today. Capture: `time · title · attendees (count or key names) · location/link`.
2. Sort chronologically. Flag back-to-back meetings and anything before 9am.
3. Return the list to `../flows/morning-brief.md`.

## Actions
None in v1. This connector is read-only.

## Outputs
- A chronological list of today's events for the brief.

## Not connected?
If the Calendar connector is unavailable, tell me and omit the schedule section of the brief.
