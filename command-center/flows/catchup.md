# Flow: Catchup

For when I've been heads-down or away — "just got out of a meeting", "what came in". Pull everything
unread from Gmail and Slack, drop anything I've already seen this session, then hand the rest to the
standard triage loop.

## Process
1. Read `../connectors/gmail.md` and `../connectors/slack.md` (skip either if not connected), plus
   `../workspace/people.md` and `../workspace/clients.md` for context (decode names, prioritize known
   client and `[VIP]` contacts).
2. Pull **all unreads** — from Gmail, unread inbox threads; from Slack, unread DMs and mentions. No time
   window; everything currently unread.
3. **Dedupe against this session.** Drop any item already surfaced earlier in our conversation (e.g. from
   a "morning brief" or an earlier catchup this session). No persistent file — session context is enough.
4. If nothing new remains, say so in one line and stop.
5. Otherwise hand the remaining items to `../flows/triage.md` and run the standard action loop (numbered
   list + rapid-fire codes, or one at a time if I ask). Catchup only gathers and dedupes — triage owns
   categorizing and acting.

## Audit (run before finishing)
- [ ] No draft was sent — replies are drafts I approve (per `triage.md`).
- [ ] Any unanswered 🔴 RESPOND item was written to `../workspace/followups.md` (handled by `triage.md`).
- [ ] Items already seen this session were not re-surfaced.
