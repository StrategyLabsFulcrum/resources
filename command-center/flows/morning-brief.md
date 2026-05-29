# Flow: Morning Brief

A read-only glance at my day. No actions taken — just a briefing. Offer to triage at the end.

## Process
1. Read `../connectors/calendar.md`, `../connectors/gmail.md`, `../connectors/slack.md`, and
   `../connectors/clickup.md` (skip any not connected).
2. Gather, in parallel where possible:
   - **Calendar** — today's events (chronological; flag back-to-backs and anything before 9am).
   - **Gmail** — urgent/unread since yesterday. "Urgent" = unread 🔴 RESPOND items (see
     `triage.md` categories). Cap at the top ~5; say how many more.
   - **Slack** — DMs and mentions I haven't read since yesterday. Cap at the top ~5.
   - **ClickUp** (if connected) — tasks due today or overdue.
3. Compose a short brief in this shape:

   ```
   Good morning. Here's {weekday}, {date}.

   📅 Today
   - {time} {event} ({attendees})
   ...

   🔴 Needs you
   - {source}: {from} — {subject}
   ...

   ✅ Due today (ClickUp)
   - {task} — {list}
   ...

   {one-line nudge: e.g. "3 things need a reply. Want to triage?"}
   ```
4. Do **not** draft, delete, or mark anything. If I say "yes, triage," follow `triage.md`.

## Audit (run before finishing)
- [ ] No messages were sent, drafted, deleted, or marked read.
- [ ] Sections for unconnected sources were omitted, not faked.
