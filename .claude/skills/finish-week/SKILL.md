---
name: finish-week
description: End of week wrap-up with review, archiving, and next week planning. Triggered automatically by /finish-day on Fridays, or manually with /finish-week.
disable-model-invocation: true
---

# Finish Week

Run AFTER `/finish-day` completes on Fridays. Daily wrap-up happens first, then this kicks in.

## 1. Build the week summary

Read all daily logs from this week (`daily/YYYY-MM-DD.md`) and current state of all project files.

For each project with activity this week:

### What got done
- List concrete accomplishments: PRs merged, decisions made, features shipped, bugs fixed
- Pull from daily logs — they're the source of truth

### What was delegated
- Check each project's `delegated.md` — what was assigned, what came back, what's overdue

### Key decisions
- Check each project's `decisions.md` for entries from this week

### What didn't happen
- Check `standup.md` history and project `my-work.md` for items that were planned but didn't get done
- Be honest about why — blocked? deprioritized? forgot?

## 2. Surface concerns

- Any delegated work that's overdue or silently stalled?
- Any deadlines approaching next week?
- Anyone whose capacity is unclear or whose work is unknown?
- Any bugs that have been open too long?
- Any Jira tickets that need updating?

## 3. Ask about next week

Ask: "What's the focus for next week? Any known meetings, deadlines, or events?"

## 4. Write weekly.md

Update `weekly.md` with:
- Week dates
- Done this week (grouped by project if multiple)
- Key decisions
- Delegated / waiting on
- Next week plan
- Risks / concerns

## 5. Archive completed items

This is the main cleanup step. For each project, go through:

### `my-work.md`
- Find all `[x]` completed items
- Move them to `archive/completed-work.md` (append, with date range header)
- Remove from `my-work.md`

### `delegated.md`
- Find all `[x]` completed items
- Move them to `archive/completed-delegated.md` (append, with date range header)
- Remove from `delegated.md`

### `bugs.md`
- Find all resolved/fixed bugs (marked `[x]` or status contains "FIXED"/"RESOLVED")
- Move them to `archive/resolved-bugs.md` (append, with date range header)
- Remove from `bugs.md`

Archive format — append to file with a week header:
```markdown
## Week of YYYY-MM-DD

- [archived item 1]
- [archived item 2]
...
```

**Don't ask for confirmation** — just do it. The items are already marked done, and they're preserved in daily logs + archive. Show the user a summary of what was archived:
- "Archived X completed tasks from {project}/my-work.md"
- "Archived Y delegated items from {project}/delegated.md"
- "Archived Z resolved bugs from {project}/bugs.md"

## 6. Commit

```bash
git add -A
git commit -m "finish week YYYY-MM-DD"
git push
```
