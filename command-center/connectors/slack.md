# Connector: Slack

Native connector tools: `mcp__claude_ai_Slack__*`. Replies are drafts I approve — use
`slack_send_message_draft`, not `slack_send_message`, unless I explicitly say "send it."

## Inputs
| Source | Tool | Scope | Why |
|---|---|---|---|
| Mentions & DMs | `slack_search_public_and_private` | messages to me / mentioning me, recent | The items to triage |
| Thread detail | `slack_read_thread` | A single thread | Read context before drafting |
| Voice | `../workspace/VOICE.md` | Full file | Draft replies in my voice |

## Process
1. Search for recent direct messages and mentions. Capture the normalized item shape:
   `source: Slack · from · channel/DM · summary · timestamp · permalink · suggested category`.
2. Suggest a category per item: 🔴 RESPOND, 🟡 FYI, 🗑️ JUNK (see `../flows/triage.md`).
3. Hand the list to the flow. `slack_read_thread` only for items I drill into or draft.

## Actions
| Code | Slack mechanism |
|---|---|
| `draft` | `slack_send_message_draft` in the right channel/DM, from `../workspace/VOICE.md`. I approve/send. |
| `read` | No API action; just stop surfacing it this session |
| `delete` | Not applicable to Slack; treat as `skip` |
| `remind` | Handled by the flow (`../workspace/todos.md`) |
| `skip` | No action |

## Outputs
- Draft messages (never sent automatically unless I say "send it").

## Not connected?
If the Slack connector is unavailable, tell me and skip it.
