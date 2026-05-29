# Flow: Triage

The action loop. Fetch recent items from my connected sources, categorize them, then let me rapid-fire
decisions. This file defines the shared vocabulary the connectors refer to.

## Shared vocabulary (source of truth)

**Normalized item shape** every connector returns:
`source · from · subject/summary · timestamp · link/id · suggested category`

**Categories:**
| | Meaning | Default handling |
|---|---|---|
| 🔴 RESPOND | Needs a reply from me | offer `draft` |
| 🟡 FYI | Worth knowing, no reply | offer `read` |
| 🗑️ JUNK | Delete it | offer `delete` |

**Action codes** (what I type against each item):
| Code | Action |
|---|---|
| `draft` | Draft a reply in my voice (read `../workspace/VOICE.md` first) |
| `remind [time]` | Append to `../workspace/todos.md` with the due time |
| `read` | Mark read (connector-specific) |
| `delete` | Dismiss it (connector-specific, always recoverable — Gmail archives, never trashes) |
| `skip` | Leave it for later |

## Process
1. Ask which sources to triage, or default to all connected ones. For each, read the matching
   `../connectors/*.md` and run its Process to fetch items in the normalized shape.
2. Present items grouped by source, numbered, each with its suggested category, e.g.:
   `3. 🔴 Jim — "Q3 numbers" — 9:14am`
3. I respond with rapid-fire codes, e.g. `1: draft, 2: remind mon 9am, 3-5: delete, 6: read`.
4. Execute each action via the relevant connector's Actions table:
   - `draft` → read `../workspace/VOICE.md`, write a draft reply via the connector (Gmail/Slack create a
     **draft**, never send), then show it to me.
   - `remind [time]` → append a line to `../workspace/todos.md`:
     `- [ ] {what} — due {time} (from {source}, {date})`
   - `read` / `delete` → per the connector's Actions table.
   - `skip` → nothing.
5. For any 🔴 RESPOND item I didn't reply to, append the sender to `../workspace/followups.md`:
   `- {person} — re: {subject} — waiting since {date}`
6. End with a one-line summary: counts per action and what's left.

## Checkpoint
After fetching but before acting, show me the categorized list and wait. I steer (re-categorize, add
sources) before any action runs.

## Audit (run before finishing)
- [ ] Every draft was created as a draft, not sent.
- [ ] Every `remind` produced a line in `todos.md`.
- [ ] Unanswered 🔴 items were added to `followups.md`.
- [ ] No connector that errored blocked the rest.
