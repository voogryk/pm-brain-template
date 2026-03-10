---
name: delegate
description: Delegate a task to a team member. Use when the user says "delegate", "assign to", "tell X to do Y", or "X is handling Y".
argument-hint: "[person] [task description] [optional: by deadline]"
---

# Delegate Task

Assign a task to a team member and track it properly.

## Parse the input

From `$ARGUMENTS`, extract:
- **Who**: person name (must match a file in `people/`)
- **What**: task description
- **When**: deadline (if mentioned — "by Friday", "EOD tomorrow", etc.)
- **Project**: infer from context, or ask if unclear

If any of these are unclear, ask the user. Don't guess.

## Update files

### 1. Project's `delegated.md`

Add a new entry under `## Active`:

```markdown
- [ ] **[task description]**
  - Who: [person name]
  - Assigned: [today's date]
  - Expected by: [deadline or "TBD"]
  - Status: Assigned
  - Notes: [any context from the user]
```

### 2. `people/{person}.md`

Add the task to their `## Current Tasks` section.

If the person doesn't have a file yet, create one from the template (`people/_template.md`) and ask the user for role/capacity info.

### 3. Offer a reminder

If there's a deadline, offer: "Want me to set a reminder to follow up on [date]?"

If yes, create the reminder in `reminders.json`.

## Confirm

Tell the user exactly what was written and where. Be specific:
- "Added to `projects/{project}/delegated.md`"
- "Updated `people/{person}.md` current tasks"
- "Reminder set for Friday 9:00"
