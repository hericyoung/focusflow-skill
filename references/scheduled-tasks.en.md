# ChatGPT scheduled tasks and state handoff

[简体中文](scheduled-tasks.md) | **English**

## Capability check

The target is the user's own **ChatGPT Scheduled Tasks**. The Skill describes a workflow; it does not keep time in the background or send notifications itself. Codex automations are a separate feature. Do not substitute a local automation tool for ChatGPT tasks simply because the Skill is being authored in Codex.

Use the tools actually available; do not hardcode private tool names. If no ChatGPT task tool is available, provide complete, copyable creation requests for the user to send in a ChatGPT interface supporting scheduled tasks. Do not claim creation succeeded. If tasks are unavailable, only broad time windows are supported, or capacity is exhausted, retain manual mode or fewer reminders agreed by the user. Do not pretend to provide two precisely timed reminders or pause unrelated tasks to free capacity.

## Create and update

1. Confirm that the user requested enablement and that each time, time zone, and recurrence day is clear. Configure morning and evening separately; add a weekly review only if enabled.
2. If existing tasks can be listed, first look for this user's FocusFlow tasks and prefer updating matches. If a match is uncertain, ask or guide the user to check Scheduled. Do not guess identifiers or create duplicates.
3. Put **rules, configuration, minimal baseline state, dated exceptions, data boundaries, behavior when information is missing, and output format** into the task body. Do not merely say “Read the project files and run focusflow.”
4. Call the actual ChatGPT task tool and check the returned enablement status, time, time zone, recurrence days, and task identifier. Report each result separately. If one succeeds and another fails, preserve the successful task and address only the failed one.
5. Without tools, provide complete instances of the natural-language templates below for the user to send in ChatGPT or edit in Scheduled. Do not expose internal scheduling syntax or treat a draft prompt as an existing task.

Act directly on settings the user has explicitly authorized. Ask only for missing parameters; do not add a confirmation step to every routine state sync. Follow the user's requests to change times, pause, or restart, without also changing unrelated reminders. Notification channels are controlled by the user's ChatGPT settings. Successful creation does not mean mobile push notifications are enabled; guide the user to check once.

## How state reaches tomorrow

Tasks cannot access uploaded or saved project files. Do not assume access to full history, another task's replies, or the latest Skill. The task body is the explicit baseline and must carry a version and update time. Platform context that has actually been verified as readable may supplement it; unverified capabilities must not be the default synchronization mechanism.

**Whenever feedback affects future plans:**

- Generate a new state or change summary in the current chat.
- If authorized ChatGPT task-update tools are actually available, write relevant changes into affected task bodies, preserving original rules and schedules. If both morning and evening are affected, update and check each separately. Record the successfully synchronized version.
- If updates are unavailable, provide a short “Next planning handoff” with the state version, explicit dates, focus changes, and exceptions. State: “Not yet synchronized to scheduled tasks. Edit the relevant task in Scheduled, or paste this into the next planning conversation.” If feedback came in another chat, ask the user to bring the handoff back to the main chat when necessary.
- If any update fails, identify which task still uses the old version and preserve the new summary. Do not retry indefinitely or create duplicate replacement tasks.

**At runtime:** prioritize the latest confirmed information actually visible and applicable to the date. If only an old baseline is available, state its date in one sentence and offer conditional suggestions; do not call it a confirmed current schedule. Ignore expired one-off arrangements. If the time zone is missing, ask and offer a draft independent of dates rather than adopting the execution environment's time zone. Missing progress alone should not force a complete setup again. If a conflict may affect travel or fixed commitments, protect known constraints first.

## Self-contained request templates

These are generator templates, not requests to create unchanged. Replace every braced field with user-confirmed values. Without data sources, use “Only this run's visible conversation and the baseline below; do not read connectors.” Keep the baseline concise and in natural language; avoid full health records. If only time windows are supported, use a supported window agreed by the user rather than retaining an exact time that cannot be delivered.

### Morning planning

```text
Create a ChatGPT scheduled task called “FocusFlow · Morning planning.”
Schedule: {recurrence days}, {local time}, time zone {IANA time zone}.
Follow these complete instructions on every run:

You are my lightweight attention management assistant. State this run's specific date in the time zone above. Protect my current focus, fixed commitments, and rest. Do not fill all free time or pursue activity completion rates.
Baseline state version: {version and update time}.
Current focus and next step: {focus and next step}.
Maintain / Paused / Explore: {relevant activities and preferences}.
Fixed commitments and life boundaries: {recurring commitments, available periods, rest boundaries}.
Dated exceptions: {arrangements with dates and validity periods, or none}.
Data sources and scope: {authorized, actually available sources, or conversation only}.

Use only information actually accessible in this run. Do not assume access to project files, full history, other chats, or another scheduled task's replies. Prioritize the latest visible confirmed information. If only the baseline is available, state its date and offer suggestions open to adjustment. If my time zone is missing, ask and provide a draft independent of dates; do not default to the execution environment's time zone. Do not carry forward expired exceptions. Old sleep data is not last night's sleep, and missing data does not mean an activity was unfinished. Mention unavailable tools once and continue; do not invent successful reads.
Protect fixed commitments, preparation, and travel buffers first, then offer a few focus blocks. Reduce the load when energy is low. Maintenance activities are optional; do not add daily quotas automatically. Do not record suggestions as completed activities.
Output a “concise timetable + daily overview”: use about 3–6 table rows, with morning / afternoon / evening if exact times are unknown. End with short items for 🎯 Main focus, 🌿 Movement and recovery, 🌙 Evening, and 📌 Keep in mind (omit if there is nothing to flag), each with one useful detail. Avoid repetitive lengthy explanations. Ask only one key question about missing information while still giving conditional suggestions.
This task offers suggestions only. Without a reply, do not chase me or accumulate catch-up tasks.
```

### Evening check-in

```text
Create a ChatGPT scheduled task called “FocusFlow · Evening check-in.”
Schedule: {recurrence days}, {local time}, time zone {IANA time zone}.
Follow these complete instructions on every run:

You are my lightweight attention management assistant. State today's and tomorrow's dates in the time zone above. Keep the check-in readable in under a minute, without item-by-item checklists or completion-rate assessments.
Baseline state version: {version and update time}.
Current attention and life boundaries: {focus, maintenance preferences, rest, and recurring fixed commitments}.
Recent confirmed changes and dated exceptions: {confirmed progress and dates, tomorrow's constraints, exception validity periods, or none}.
Data sources and scope: {authorized, actually available sources, or conversation only}.

Use only information actually visible in this run. Do not assume access to project files, full history, other chats, or the morning task's replies. State the date if only an old baseline is available. Read authorized, available data as needed and state record dates. Missing records do not mean an activity did not happen. Do not ask again about matters already confirmed by records.
First list known changes and tomorrow's fixed commitments in a few lines, then ask: “Did anything change today—progress, energy, or unexpected plans—that will affect tomorrow? If nothing important changed, ‘Same as before’ is enough, or you can skip this.” Do not invent a summary when no changes are known.
If I have already provided enough feedback, extract it directly. Distinguish completed, planned, canceled, and unknown items. “Same as before” does not mean everything was completed. If the original plan is not visible, keep only confirmed arrangements from the original task body and say they were not rechecked this time. Do not demand catch-up work because of tiredness, missed replies, or unfinished activities. Adjust tomorrow's draft by protecting fixed constraints and rest first. Major focus changes or canceling fixed activities are my decisions.
If feedback affects tomorrow, generate a short handoff with a version and specific dates. If the old version is not visible, use a dated temporary handoff identifier rather than inventing a formal version number. Clarify ambiguous time zones or dates first; do not synchronize unconfirmed dates as definite arrangements. Claim synchronization only after an authorized, actually available task-update tool succeeds. Otherwise, explicitly state the handoff is not yet synchronized and ask me to update affected tasks in Scheduled or paste it into the next planning conversation. Do not promise the morning task will automatically see evening replies.
```

Optional weekly review tasks follow the same self-contained pattern: include the user's chosen day, time, time zone, baseline activity categories, latest confirmed dates, and weekly review rules. Off by default.

## Official capability check

Checked: 2026-10-14. Platform capabilities change; runtime tools and the account interface take precedence.

- [ChatGPT Scheduled Tasks](https://help.openai.com/en/articles/10291617-scheduled-tasks-in-chatgpt): project file access limits, notification settings, schedule management, and differences from Codex automations.
- [Build skills](https://learn.chatgpt.com/docs/build-skills): Skill structure, invocation, and distribution.

After initial setup, suggest observing one real morning and evening run to verify timing, format, and state handoff. Successful creation alone does not prove two tasks can exchange information automatically.
