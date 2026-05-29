# Setup (run once)

Onboard me to Command Center. This configures the workspace; it does not process any messages.

## Process
1. **Check connectors.** Probe each native connector and report which are live:
   - Gmail (`mcp__claude_ai_Gmail__list_labels`)
   - Slack (`mcp__claude_ai_Slack__slack_search_channels`)
   - Google Calendar (`mcp__claude_ai_Google_Calendar__list_calendars`)
   - ClickUp (optional) (`mcp__claude_ai_ClickUp__clickup_get_workspace_hierarchy`)
   Tell me what's connected and what to connect in Claude's connector settings if I want more. Don't
   block on missing ones.
2. **Seed my voice.** If `workspace/VOICE.md` is still the template, probe how I write — ask as
   **structured multiple-choice questions** where possible (use the AskUserQuestion picker if your
   environment supports it; otherwise ask in chat, one at a time). Aim for concrete signal, not vague
   adjectives:
   - **Tone** (multi-select): concise · warm · direct · formal · playful · numbers-forward ·
     skip-pleasantries
   - **Casual sign-off** (choose or write in): "Thanks — Scott" · "—S" · "Cheers, Scott" · other
   - **Formal sign-off** (choose or write in): "Best, Scott" · "Best regards, Scott Ellis" · other
   - **Never-use phrases** (free text): clichés I avoid (e.g. "circling back", "per my last email")
   - **One real example** (free text): paste 1–2 sentences from a reply I'm happy with
   Write the answers into `workspace/VOICE.md` under its existing headings.
3. **Seed people & clients.** Ask (structured where possible, otherwise in chat) — no inbox scan, just
   ask me:
   - "Who are your top 3–5 clients right now?" For each: one line on what we do + the key contact.
     Write into `workspace/clients.md`.
   - "Who do you deal with most?" For each: name/nickname, full name, role, org. Write into
     `workspace/people.md`; flag anyone important with `[VIP]`.
   Keep both short — they grow as I work.
4. **Confirm workspace files exist.** Ensure `workspace/todos.md`, `workspace/followups.md`,
   `workspace/VOICE.md`, `workspace/people.md`, and `workspace/clients.md` are present (create from
   template if missing).
5. **Point me at the triggers.** Tell me I can now say "morning brief" or "triage" — and that
   everything lives in plain markdown I can edit by hand.

## Done when
- I know which connectors are live.
- `VOICE.md` reflects how I actually write.
- `people.md` and `clients.md` have my top contacts and active clients.
