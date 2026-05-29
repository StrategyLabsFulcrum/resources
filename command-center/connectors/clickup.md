# Connector: ClickUp (optional)

Native connector tools: `mcp__claude_ai_ClickUp__*`. **Scan-only in v1** — surface what's assigned to
me and due/overdue. No task creation, no status changes.

## Inputs
| Source | Tool | Scope | Why |
|---|---|---|---|
| My tasks | `clickup_filter_tasks` | assigned to me, not closed, ordered by due date | My ClickUp "inbox" |
| Task detail | `clickup_get_task` | A single task | Only if I ask about one |

## Process
1. `clickup_filter_tasks` for open tasks assigned to me. Capture:
   `name · list/space · status · due date · url`.
2. Flag overdue and due-today. Group the rest by due date.
3. Return the list to the caller (`triage` includes it as a source; `morning-brief` shows due-today).

## Actions
None in v1 (scan-only). If I want to act on a task, open its url.

## Outputs
- A list of my open ClickUp tasks, overdue/due-today flagged.

## Not connected?
ClickUp is optional. If the connector is unavailable, silently skip it — do not prompt me to connect it.
