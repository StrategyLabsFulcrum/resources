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
1. Ask two quick things (if I just say "triage", default to all sources + batch style):
   - **Which sources?** All connected, or a specific one ("just Slack").
   - **Which style?** **Batch** (default) or **one at a time** — see Triage styles below. Phrases like
     "walk me through it" or "one at a time" pick the second.
   Read the matching `../connectors/*.md` for each source and run its Process to fetch items in the
   normalized shape.
2. **Categorize** each item (🔴 / 🟡 / 🗑️). Consult `../workspace/people.md` and
   `../workspace/clients.md`: recognize the sender, decode names/shorthand so summaries read in plain
   names, and bump known **client contacts** and `[VIP]` people toward 🔴.
3. Present and act according to the chosen style (see Triage styles). If an unfamiliar name recurs
   across items, offer to add a one-line entry to `../workspace/people.md` (only with my ok — never add
   silently).
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

## Triage styles

### Batch (default) — numbered list, rapid-fire
Present every item as ONE continuously numbered list, `1…N`, even across sources. Group visually under a
source subhead, but keep the numbers running continuously so ranges work. One item per line:

`N. <category> <from> — "<subject/summary>" — <time>`

Example:
```
Gmail
1. 🔴 Jim — "Q3 numbers" — 9:14am
2. 🟡 Acme Newsletter — "Weekly digest" — 8:02am
3. 🗑️ Promo — "50% off today" — 7:31am
Slack
4. 🔴 Jane (DM) — "can you review the brief?" — 9:40am
5. 🟡 #campaigns — mentioned you — 9:05am
```
Then I reply with rapid-fire codes by number or range:
`1: draft, 2: read, 3: delete, 4: draft, 5: read`   or   `1,4: draft · 2,5: read · 3: delete`.
Apply them in order, then confirm what you did.

### One at a time — you recommend, I confirm
A more deliberate pass. Go through items highest-priority first (🔴 → 🟡 → 🗑️). For each item:
- Show just that item (its number, from, subject, time) and a one-line gist if it helps.
- **Recommend one action with a short why**, e.g. *"Recommend `draft` — Jim's asking for the Q3 figures
  and you usually reply same-day."*
- Wait. I confirm (`y` / Enter accepts your rec) or override with any action code.
- Execute, then move to the next item. One item, one recommendation, one decision.

## Checkpoint
**Batch:** after fetching, show the full numbered list and wait — I steer (re-categorize, add sources)
before any action runs. **One at a time** is checkpointed by design — you pause on every item.

## Audit (run before finishing)
- [ ] Every draft was created as a draft, not sent.
- [ ] Every `remind` produced a line in `todos.md`.
- [ ] Unanswered 🔴 items were added to `followups.md`.
- [ ] No connector that errored blocked the rest.
