# Setup and state

[简体中文](setup-and-state.md) | **English**

## Progressive setup

Introduce the workflow in one sentence: FocusFlow protects your main focus and long-term interests, suggests a plan in the morning, and checks only for changes in the evening. Ask no more than about three related questions per round. Allow “Not sure yet” and skipping optional items. Do not ask again for information already provided.

Suggested first round:

> Let's do a light setup: what would you most like to move forward, and which interests would you like to keep? What is your time zone? On which days and at what times would you like morning planning and evening check-ins, or would you prefer to try manually first?

Without timing answers, offer the manual workflow first. You may suggest candidate times, but do not treat them as agreed settings. Time zones must be unambiguous, such as Asia/Shanghai. “Beijing time” can be resolved and restated, while “local time” or “CST” needs clarification. Use the user's routine, not fixed defaults of 09:30 / 23:30; evening check-ins need not be late at night. In daylight saving regions, confirm local clock time. Do not change to a destination's time zone automatically when the user travels.

Then fill only gaps that affect planning:

| Setting | What to establish |
|---|---|
| Activity list | Focus, Maintain, Paused, Explore, and current next steps; no complete task breakdown required |
| Life boundaries | Usual available periods, fixed commitments, rest, and time the user does not want scheduled; broad descriptions are fine |
| Reminders | Whether morning and evening are each enabled, their times, time zone, and recurrence days; weekends can differ or be off |
| Response preference | Concise timetable + daily overview by default; whether to be shorter or more detailed |
| Weekly review | Optional; ask for day and time only if enabled |
| Data sources | This chat by default; optionally authorized and available calendar, sleep, or exercise sources |

Health connections are not required. Do not assume an Apple Watch, Apple Health, or any specific plugin. If the user chooses a connection, ask only for the necessary scope and verify actual access in this run. Interactive chat access does not imply scheduled-run access. Using the Skill does not require creating Notion pages, a database, or an integration.

## Complete setup

Generate a configuration summary with the time zone, morning/evening enablement and recurrence, activity categories, life boundaries, data sources, and weekly review setting. Ask the user to check settings that remain unconfirmed. Do not repeatedly ask for approval of times already explicitly supplied with a request to create reminders.

Do not create scheduled tasks until required parameters are clear. If the user wants to try first, provide a manual plan directly. Once times, time zone, and recurrence days are clear and the user requests enablement, create or update using [Scheduling and handoff](scheduled-tasks.en.md).

At the end of initialization, deliver:

1. Confirmed settings and an initial activity list.
2. A plan appropriate to the actual time of day. If it is already late, start with an evening check-in or tomorrow's draft; do not schedule time that has already passed.
3. The actual creation status of the two reminders, or clearly labeled prompts pending manual creation. List an optional weekly review separately.

## FocusFlow State

Maintain a short, copyable state summary in the conversation. Generate it after initialization, important changes, and weekly reviews. Day to day, show only changes; output the full version when the user wants to export or move to another chat.

Record the following. Mark unknown fields “Unconfirmed” rather than filling them in yourself:

- **Version and time**: an incrementing version, update time, and user time zone. If the previous version is not visible, use a dated temporary handoff identifier instead of inventing a formal version number; increment when merging back into known state. Mark unconfirmed dates as pending confirmation, and do not write them into tasks as confirmed exceptions.
- **Configuration**: language, morning/evening reminder times and recurrence days, weekly review setting and time, and reading preferences.
- **Attention**: activity names, categories, next steps, optional desired intervals of attention, and latest confirmed progress with dates.
- **Fixed boundaries**: recurring commitments, rest periods, and unavailable time.
- **Recent exceptions**: specific dates, details, and validity periods; distinguish canceled from unconfirmed items.
- **Data basis**: user reports or actually retrieved sources and record dates; keep only the summary needed for planning.
- **Reminder status**: names, tool-returned identifiers if available, created / pending creation / paused, and the state version successfully synchronized.

For contradictions on the same date, use the user's latest explicit correction. If you cannot determine which is newer, ask one key question. Keep a few key changes with each new version. Do not silently overwrite history and then claim precise activity counts across months.

For a conversation summary, say only “Organized in this chat.” Claim successful saving or synchronization only after an actual write or tool update succeeds. If the user wants project materials, guide them to save the latest summary and label older versions. Do not claim the chat automatically updates uploaded files. When moving chats, have the user bring the latest summary rather than relying on invisible history.

## A complete example (fictional)

Confirmed by the user: Asia/Shanghai; weekday morning reminder at 08:45 and evening check-in at 21:15; weekly review off; main focus is writing a course outline; maintain walking and reading; fixed meeting on Tuesday 14:00–15:00; no data connections.

Record these settings in the initial summary. If the next step for the focus is missing, suggest “List three course modules” and mark it pending confirmation. Do not add reading quizzes or turn walking into a compulsory daily quota. After creating the two tasks, check each result and suggest a plan for the remaining time today. If task tools are unavailable, supply two complete prompts with these settings and mark the status “Pending manual creation.”
