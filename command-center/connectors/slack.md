# Connector: Slack

Native connector tools: `mcp__claude_ai_Slack__*`. Replies are drafts I approve — use
`slack_send_message_draft`, not `slack_send_message`, unless I explicitly say "send it."

## Inputs
| Source | Tool | Scope | Why |
|---|---|---|---|
| Mentions & DMs | `slack_search_public_and_private` | messages to me / mentioning me, recent | The items to triage |
| My own recent messages | `slack_search_public_and_private` | messages from me, last ~2 weeks | Detect commitments I made (Process 3) |
| Thread detail | `slack_read_thread` | A single thread | Confirm a question went unanswered / a commitment had no follow-up |
| Voice | `../workspace/VOICE.md` | Full file | Draft replies in my voice |

## Process
Run three passes and merge into one list. Each item uses the normalized shape:
`source: Slack · from · channel/DM · summary · timestamp · permalink · suggested category`.

1. **Unread mentions & DMs.** Search recent direct messages and @-mentions of me. Categorize each
   🔴 RESPOND / 🟡 FYI / 🗑️ JUNK (see `../flows/triage.md`).

2. **Open questions to me.** Find recent DMs and threads I'm in where the most recent message is a
   question directed at me (or clearly awaiting my input) and I have **not** replied since. Read the
   thread (`slack_read_thread`) to confirm there's no later message from me. Surface as 🔴 RESPOND
   flagged `(open question — you haven't replied)`.

3. **Open commitments I made.** Search my own messages from the last ~2 weeks for commitment language —
   "I'll …", "let me …", "I'll look into / find / send …", "on it", "will do", "I can get you …",
   "by {day}". For each hit, read the thread and check whether I later posted a follow-up that **delivers
   or closes it**. If there's no closing follow-up, surface as 🔴 RESPOND flagged
   `(you committed — no follow-up since {date})`, and suggest `remind` (put it on `todos.md`) or `draft`
   (deliver it now).

Dedupe across passes — one thread = one item, keeping the strongest flag. The flag rides in the item's
summary so the numbered triage list shows *why* it surfaced. Read threads for candidates only; don't
crawl every message. Hand the merged list to the flow.

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
