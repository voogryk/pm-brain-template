---
name: start-day
description: Morning kickoff routine. Use when the user starts a session, says "start day", "morning", "let's go", or opens a new conversation at the beginning of the day.
---

# Start Day Routine

Execute these steps in order:

## 1. Pull latest from all repos

If the pm-brain repo is tracked with git, pull latest:

```bash
git pull
```

<!-- If you have sibling project repos, add git pull commands for them here. Example: -->
<!-- git -C /path/to/your-project-api pull -->
<!-- git -C /path/to/your-project-web pull -->

If any pull fails (merge conflict, auth issue), report it immediately — don't silently skip.

## 2. Read all core files

Read these files to load full context:

**Cross-project:**
- `inbox.md`
- `standup.md`

**All project files:**
For each project folder in `projects/`, read:
- `my-work.md`
- `delegated.md`
- `bugs.md`
- `decisions.md` (if exists)

## 3. Check today's reminders

Read `reminders.json` and check for any pending reminders due today. Include them in the briefing under a "Reminders" section so the user knows what's coming up.

## 4. Read all people files

```bash
ls people/*.md
```
Read every person file (skip `_template.md`). Know who's doing what.

## 5. Check yesterday's daily log

```bash
ls daily/ | sort | tail -1
```
Read the latest daily file if it exists — know what happened last session.

## 6. Check open PRs

<!-- Customize with your GitHub org/repos. Example: -->
<!-- gh pr list --repo your-org/your-repo --state open 2>/dev/null -->

If you have repos configured in `.claude/rules/`, check their open PRs.
PRs are actionable — they need review, approval, or merge. Surface anything that's been open too long.

## 7. Build the morning briefing

Present to the user:

### a. Overdue / due today
Check all project `delegated.md` files for anything past its expected date or due today. Call it out directly.

### b. Blocked items
List everything blocked and on whom.

### c. Follow-ups needed
Check all `people/*.md` follow-up sections. Surface anything that needs chasing today.

### d. Unknowns
Anyone whose current task is unclear (marked with `[?]`)? Flag it — need to find out on next daily.

### e. Open bugs
List all open bugs from project `bugs.md` files. Ask: "Which of these bugs do you want to tackle today?" Let the user pick — add selected bugs to the day's plan in standup.

### f. Today's plate
Suggest what the user should focus on today based on priorities and what's unblocked.

## 8. Ask

- "Anything new from Slack/Jira overnight?"
- "Any changes to what I just summarized?"

## 9. Build today's plan & standup

After the user confirms / adds info, build the day plan. Write into `standup.md` with `Last updated: YYYY-MM-DD`:
- **Yesterday**: from daily log
- **Today**: planned tasks based on priorities and what user said
- **Blockers**: anything currently blocked and on whom
- **Need to Follow Up**: people/items that need chasing

Then give a short, copy-paste-ready standup:

```
**Yesterday:**
- [concrete things done, from daily log]

**Today:**
- [planned tasks for today]

**Blockers:**
- [blocked items and who's blocking them, or "None"]
```

Keep the standup concise — meant to be dropped into Slack or said in a meeting. No fluff.
