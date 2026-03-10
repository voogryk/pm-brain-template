---
name: finish-day
description: End of day wrap-up routine. Use when the user says "finish day", "wrap up", "end of day", or similar.
---

# Finish Day Routine

**Important**: Ask questions ONE AT A TIME. Wait for the answer before moving to the next. Don't dump everything at once.

## 1. Read current state

Read all core files (project files + cross-project files) + people files to know what's current.

## 2. Review today's plans

Check `standup.md` for what was planned today. For each item that isn't marked done:
- Ask: "Did you finish [task]?"
- If yes: mark it done in the relevant project file
- If no: ask if it carries over to tomorrow or if something changed
- Do this ONE task at a time

## 3. Check delegated items

For each delegated item (in any project's `delegated.md`) that had an expected delivery today:
- Ask: "Did [person] deliver [task]?"
- Update status based on answer

## 4. Capture new stuff

Ask: "Anything new come in today that we haven't captured? Slack messages, Jira updates, decisions, things someone said?"
- Write whatever they say to the right project files immediately

## 5. Tomorrow preview

Ask: "What do you want to focus on tomorrow?"
- If they're not sure, suggest based on priorities and what's unblocked

## 6. Write daily log

Create `daily/YYYY-MM-DD.md` with a full record of the day. This is the **permanent reference** — future sessions will read this to understand what happened.

Include:
- **What was accomplished** — concrete things done, PRs merged, decisions made, docs written
- **What was discussed/decided** — any important conversations, direction changes
- **Status changes** — tasks that moved, things that got blocked/unblocked
- **Delegated updates** — what was assigned, what came back, what's overdue
- **Carries over** — what didn't get done and why
- **Tomorrow's plan** — what's intended for next day

## 7. Update files

- Move completed items appropriately in the relevant project files
- Update `standup.md` for tomorrow if possible
- Update `weekly.md` with this day's progress

## 8. Commit and push pm-brain

Commit all changes made during the session and push so nothing is lost:

```bash
git add -A
git commit -m "daily update YYYY-MM-DD"
git push
```

## 9. Pull latest from all repos

Pull fresh code so the server has the latest state overnight / for next session:

```bash
git pull
```

<!-- Add pulls for your sibling project repos here. Example: -->
<!-- git -C /path/to/your-project-api pull -->

## 10. Friday check — trigger /finish-week

Check what day of the week it is:

```bash
date +%u
```

If it's **Friday (5)**, tell the user: "It's Friday — let's do the weekly wrap-up too!" and invoke the `/finish-week` skill. This handles:
- Week summary and review
- Archiving completed items from all project files
- Next week planning

If it's NOT Friday, skip this step.

## 11. Cheer them up

End the session with a silly, warm "good job" moment. The user WANTS this — even if it's cringe, go for it. Think:
- Highlight what actually moved forward
- If it was a grind day with lots of blocked stuff, acknowledge that managing blockers IS work
- Throw in something fun — a dumb metaphor, a compliment, a "you're a beast", whatever feels right
- Cringe is OK. Corporate is not. Be a hype friend, not an HR email
- Make them smile before they close the terminal
- If it's Friday — make it extra good, they earned the weekend
