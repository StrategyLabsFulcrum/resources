# Flow: Wind Down

An end-of-day closeout. Preview tomorrow, surface what I'm on the hook for tomorrow, then force a pass
through today's open Slack loops — one at a time — so I close or consciously defer each before I sign off.

## Process
1. Read `../connectors/calendar.md` and `../connectors/slack.md`, the ledger (`../workspace/todos.md`,
   `../workspace/followups.md`), and `../workspace/people.md` + `../workspace/clients.md` for context
   (decode names, prioritize client/`[VIP]` people). Skip any connector that isn't set up.

2. **Tomorrow at a glance.** From calendar, list tomorrow's events (chronological; flag early starts,
   back-to-backs, and anything that needs prep tonight). Call out the first commitment of the day.

3. **Due tomorrow.** Surface what I'm on the hook for tomorrow: `todos.md` items due tomorrow, plus any
   commitment (from `slack.md` pass 3 or `followups.md`) where I said I'd deliver "by tomorrow", "first
   thing", or a date that lands tomorrow. This is the "don't get blindsided at 9am" list.

4. **Close the loops — one at a time.** This is the point of wind-down. Pull today's open Slack loops —
   run passes 2 and 3 in `slack.md` (open questions to me + my unfulfilled commitments) — plus any aging
   entries in `followups.md`. Then go through them **one at a time** using the one-at-a-time style in
   `triage.md`: show the single loop, recommend how to close it, and wait. The goal is a decision before
   sign-off — don't let me skip silently. For each loop, offer:
   - `draft` — a reply that closes it now, or a short holding reply ("got this — I'll have it to you by
     {when}"). Drafts only; I approve/send.
   - `remind [time]` — if it genuinely can't close tonight, log it to `todos.md` with a due time so it
     isn't dropped.
   - **mark handled** — I already dealt with it; remove the matching line from `followups.md`.
   - `skip` — leave it, but say so out loud. A conscious choice, not an oversight.
   Move to the next loop only after I've decided on the current one.

5. **Sign-off summary.** One short wrap: loops closed vs. deferred (and where the deferred ones landed —
   `todos.md` / `followups.md`), plus tomorrow's first meeting. End on a clean "you're clear to sign off."

## Notes
- Drafts, never auto-sends (same rule as everywhere). Closing a loop = a draft I approve, a logged
  reminder, or marking a followup handled.
- `remind` appends to `todos.md` per `triage.md`; "mark handled" removes the line from `followups.md`.
- If calendar or Slack isn't connected, say so and do what you can with the ledger.

## Audit (run before finishing)
- [ ] Every open loop got an explicit decision — none skipped silently.
- [ ] Anything not closed tonight landed in `todos.md` (with a due time) or stayed in `followups.md`.
- [ ] No message was sent automatically — replies are drafts I approve.
