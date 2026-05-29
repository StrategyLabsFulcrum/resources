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
2. **Seed my voice.** If `workspace/VOICE.md` is still the template, ask me 3 short questions,
   one at a time, and write my answers in (ask for concrete examples, not adjectives):
   - "Paste 1–2 sentences from a reply you're happy with."
   - "How do you sign off — casual and formal?"
   - "Any words or phrases you never use?"
   Save them into `workspace/VOICE.md`.
3. **Confirm workspace files exist.** Ensure `workspace/todos.md`, `workspace/followups.md`, and
   `workspace/VOICE.md` are present (create from template if missing).
4. **Point me at the triggers.** Tell me I can now say "morning brief" or "triage" — and that
   everything lives in plain markdown I can edit by hand.

## Done when
- I know which connectors are live.
- `VOICE.md` reflects how I actually write.
