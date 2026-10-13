# FocusFlow

[简体中文](README.md) | **English**

**Protect your attention with ChatGPT, and make room for lasting interests.**

Plan in the morning. Share changes in the evening. No item-by-item checklists, and no need to fill every hour.

## Get started in ChatGPT

The **ChatGPT mobile app** is recommended; the web version works too. Start in a dedicated chat. **Scheduled reminders, health data, and calendar connections are optional.**

### Start a new chat and send this prompt

Open ChatGPT, create a dedicated chat, and send the prompt below so it can try reading the project files directly:

```text
Please visit the FocusFlow project and help me start managing my daily attention using its rules:
https://github.com/hericyoung/focusflow-skill

Actually open and read these two files in full, rather than relying on the repository introduction or search snippets:
1. https://github.com/hericyoung/focusflow-skill/blob/main/SKILL.en.md
2. https://github.com/hericyoung/focusflow-skill/blob/main/references/setup-and-state.en.md

After reading, briefly state which files you accessed. Then learn about my current focus, long-term interests, routine, and time zone. Ask no more than three questions per round. Please respond in English.
Start manually, without creating reminders or connecting external tools. Leave uncertain settings blank.
Once you understand my situation, give me a concise plan and a daily overview.

If you cannot access a file or can only read part of it, say what is missing and ask me to provide it. Do not pretend you have read it in full.
```

Answer in your own words. “Not sure yet” or “Skip for now” is fine. If a plan needs adjusting, say “Make today lighter,” “Keep it shorter,” or “I already have something scheduled then.”

This method requires web access in the current chat and may not always work. It uses the workflow within your conversation; it does not automatically install a Skill. [Official web search documentation](https://learn.chatgpt.com/docs/web-search)

<details>
<summary>Cannot read the GitHub files? Start manually</summary>

First send: “I will send the workflow files. Until I say ‘All materials sent,’ please only acknowledge receipt.”

Open the two files below and send the **full contents** of each to the same chat:

- [First: core workflow, SKILL.en.md](SKILL.en.md)
- [Second: setup and state](references/setup-and-state.en.md)

If only one file is missing, send just that file. You do not need to copy this README.

If the file page has a **Raw** option, open it to copy the plain text. If a message is too long, split it at paragraph boundaries and label each part with the file name and part number.

Finally send: “All materials sent. Please begin using the startup instructions above.”

</details>

### Use it day to day

Return to the same chat and describe what you need. There is no need to resend the files.

| When | What you might say |
|---|---|
| ☀️ Morning | Plan today for me, with a timetable and daily overview. |
| ↪ Plans change | Something came up this afternoon. Move my main focus to the evening and reduce the rest. |
| 🌙 Evening | I made some progress on my main focus, but I am tired. Make tomorrow lighter. |

If nothing important has changed, say “Same as before” or skip the check-in. For a review, ask: “Help me review this week and decide what to continue, reduce, or pause.”

**You are ready to use FocusFlow.** Everything below is optional; daily planning works without it.

## Optional features and other environments

<details>
<summary><strong>⏰ Scheduled reminders: have ChatGPT prompt me</strong></summary>

Send this request in the original chat, replacing the bracketed fields:

```text
I would like to enable FocusFlow scheduled reminders.
First, read the scheduling and handoff rules in full:
https://github.com/hericyoung/focusflow-skill/blob/main/references/scheduled-tasks.en.md
If you cannot read them, ask me to provide the contents before configuring anything.

Time zone: [for example, America/New_York]
Morning planning: [days and preferred time or time window]
Evening check-in: [days and preferred time or time window, or leave off]
Weekly review: leave off for now.
Check which scheduling options my account actually supports, and report whether each reminder was created successfully.
If creation is unavailable, mark it as “pending creation” and provide a complete request I can copy.
```

Available time windows, exact times, and task limits depend on your account. Check the actual creation result. If tasks are unavailable, use a phone alarm to remind yourself to open the chat. [Official scheduled tasks documentation](https://help.openai.com/en/articles/10291617-scheduled-tasks-in-chatgpt)

After creation, check the time zone, recurrence, and notification permissions, then observe an actual run. **A draft prompt does not mean a reminder has been created.**

If today's changes affect the next reminder, add:

```text
Sync these changes to the affected reminders. If you cannot update them, give me a handoff summary I can copy and explain where to put it.
```

</details>

<details>
<summary><strong>🌿 Health data: consider sleep and exercise</strong></summary>

The simplest option is to say: “I slept six hours last night and feel tired today.” You can adjust a plan without connecting any data.

If your account has **Health**, follow the instructions in the ChatGPT iPhone app to connect Apple Health and authorize the sleep or exercise data you want to share. See the [official Health documentation](https://help.openai.com/en/articles/20001036-health-in-chatgpt) for eligibility and setup.

After connecting, try this in your FocusFlow chat:

```text
@Health Read last night's sleep and my latest exercise record. List the data you actually retrieved and its dates, then adjust today's plan.
If the data is unavailable or outdated, say so. I can provide an update manually.
```

Check that the dates are correct. Access in a chat does not guarantee access on every scheduled run. If reading fails, continue planning from your own description of your energy level.

</details>

<details>
<summary><strong>💻 Other environments: Codex or an Agent that supports Skills</strong></summary>

Install this repository using your product's Skill installation method, keeping `SKILL.md` and `references/` in their relative locations. The standard installation entry point is `SKILL.md`; [SKILL.en.md](SKILL.en.md) is the English reading and chat-use version of the same rules. Then invoke FocusFlow:

```text
Help me start FocusFlow with manual morning planning and evening check-ins.
Learn about my current focus, long-term interests, and routine. Do not create reminders yet. Please respond in English.
```

The core workflow can be reused. Reminders, notifications, health data, and state storage depend on the product's actual capabilities. Other Agents have not been individually verified. Installing a Skill does not add these capabilities by itself.

Codex automations and ChatGPT scheduled tasks are separate features. Personal state and reminders do not automatically transfer between environments. When switching, bring your latest state summary and check existing reminders on the original platform. [Official explanation of the platform differences](https://help.openai.com/en/articles/10291617-scheduled-tasks-in-chatgpt)

</details>

<details>
<summary><strong>📋 Back up your settings or move to a new chat</strong></summary>

Send this in the original chat:

```text
Export my latest FocusFlow state summary, including my current focus, confirmed settings, fixed commitments, recent exceptions, and reminder status.
```

Save the summary. In a new chat, send the startup prompt above and your summary, asking it to continue from the existing state. If reminders are enabled, also ask it to read the scheduling rules and check existing reminders before creating anything new. If file access fails, provide the contents manually.

If you cannot find the old records, describe your current situation again. There is no need to reconstruct every past day. Moving to a new chat does not cancel old reminders.

</details>

## How it works

<details>
<summary><strong>Curious about how FocusFlow plans? Read more</strong></summary>

FocusFlow is a set of written rules for an AI to follow. Using the currently visible conversation and state summary, it repeats three steps:

1. **Understand your situation:** record your focus, interests, fixed commitments, routine, and next step.
2. **Suggest a plan:** protect fixed commitments and rest first, then make time for your main focus and, when energy allows, other interests.
3. **Adjust to changes:** evening or ad hoc feedback updates only what affects future plans, without requiring item-by-item checklists.

Activities default to **Focus, Maintain, Paused, and Explore**. You can use your own categories instead. A plan is not a completion record, a missed reply is not a failure, and unfinished activities do not accumulate as catch-up obligations.

The platform runs scheduled reminders. Each task needs the necessary rules and baseline state. Evening feedback requires an explicit handoff; morning tasks cannot be assumed to see it automatically.

| Workflow file | Contents |
|---|---|
| [SKILL.en.md](SKILL.en.md) | Core principles and daily workflow |
| [Setup and state](references/setup-and-state.en.md) | Personal settings and state summaries |
| [Scheduling and handoff](references/scheduled-tasks.en.md) | Optional reminders and state synchronization |

</details>

## Design choices and limitations

<details>
<summary><strong>Why is there no calendar connection by default?</strong></summary>

This is my personal preference: I do not like putting recurring daily activities such as reading, exercise, and hobbies into a calendar app. It makes the calendar look crowded and adds maintenance. I prefer an adjustable plan through a daily conversation.

If you enjoy using a calendar, discuss adding a calendar MCP, Skill, or another connection with ChatGPT—for example, to read fixed commitments or write selected time blocks. What is possible depends on the tools and permissions in your environment. This repository does not include a calendar integration.

</details>

<details>
<summary><strong>What are the limits of conversation-based state? Can I connect a database?</strong></summary>

State currently relies on **conversation context and state summaries**, without a separate database. As a conversation grows, earlier details may no longer be visible. Moving between chats requires a summary, and this approach is not suitable for precise statistics across months of activity.

Export a summary after important changes as a backup. If you need long-term storage, queries, or statistics, you can connect tools such as **Notion or Supabase** yourself and discuss the recording process with ChatGPT. This Skill does not provide a ready-made database schema or automatic read/write workflow. You will still need to define the source of truth and when updates happen.

Plan quality also depends on accurate, current information. Correct omissions or mistakes directly. You decide whether to act, reduce the load, or change your focus. Verify actual reminders, notifications, and state handoffs in your own account.

</details>

---

[MIT License](LICENSE) · Use, modify, and share freely. When reporting issues, use anonymized examples and avoid including private chats or health records.
