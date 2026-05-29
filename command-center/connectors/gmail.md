# Connector: Gmail

Native connector tools: `mcp__claude_ai_Gmail__*`. No send and nothing is ever trashed — replies are
drafts I approve in Gmail; `delete` means **archive** (our team archives, never deletes). Reads and
archives are done with labels.

## Inputs
| Source | Tool | Scope | Why |
|---|---|---|---|
| Inbox threads | `search_threads` | `in:inbox newer_than:2d` (or since I last triaged) | The items to triage |
| Thread detail | `get_thread` | A single thread id | Read full context before categorizing/drafting |
| Voice | `../workspace/VOICE.md` | Full file | Draft replies in my voice |

## Process
1. `search_threads` for recent inbox threads. For each, capture the normalized item shape:
   `source: Gmail · from · subject · timestamp · thread_id · suggested category`.
2. Suggest a category per item: 🔴 RESPOND, 🟡 FYI, or 🗑️ JUNK (see `../flows/triage.md`).
3. Hand the list back to the flow for the action loop. Only `get_thread` for items I drill into or draft.

## Actions (mapped to the shared action codes)
| Code | Gmail mechanism |
|---|---|
| `draft` | `create_draft` as a reply on the thread, written from `../workspace/VOICE.md`. I send it myself. |
| `read` | `unlabel_thread` removing the `UNREAD` label |
| `delete` | **Archive**, not trash — `unlabel_thread` removing the `INBOX` label. Stays in All Mail, fully recoverable. We archive, we don't delete. |
| `remind` | Handled by the flow (writes to `../workspace/todos.md`); no Gmail action |
| `skip` | No action |

## Outputs
- Draft replies in Gmail (never sent automatically).
- Label changes: read = remove `UNREAD`; archive = remove `INBOX`. Nothing is trashed.

## Not connected?
If `list_labels` errors or the Gmail connector is unavailable, tell me Gmail isn't connected and skip it.
