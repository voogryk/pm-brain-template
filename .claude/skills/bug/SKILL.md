---
name: bug
description: Log a new bug. Use when the user reports a bug, says "found a bug", "there's an issue with", or wants to track a defect.
argument-hint: "[description] [optional: severity P0-P3]"
---

# Log Bug

Quickly capture a bug and file it in the right project.

## Parse the input

From `$ARGUMENTS` and conversation context, extract:
- **Description**: what's broken
- **Severity**: P0 (critical), P1 (high), P2 (medium), P3 (low) — if not specified, ask
- **Project**: infer from context. Ask if unclear.

## Write to bugs.md

Add a new entry under `## Open` in the project's `bugs.md`:

```markdown
- [ ] **[short title]**
  - Added: [today's date]
  - Severity: [P0/P1/P2/P3] — [one word: Critical/High/Medium/Low]
  - Details: [description of what's broken, how to reproduce if known]
  - Status: Open
```

If the user provides root cause analysis, reproduction steps, or fix ideas — include them.

## Confirm

Tell the user:
- What was logged
- Where it was written
- The severity assigned
- Ask: "Anything else to add? Root cause ideas? Who should fix it?"
