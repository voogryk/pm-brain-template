---
name: decide
description: Log an important decision. Use when the user says "we decided", "decision made", or describes a technical/product/organizational choice.
argument-hint: "[what was decided]"
---

# Log Decision

Capture an important decision so future-you knows "why did we do that?"

## Gather info

From `$ARGUMENTS` and conversation, extract:
- **What was decided**: the actual decision
- **Context**: what prompted this — a meeting, a problem, a discussion
- **Who was involved**: people who participated in the decision
- **Impact**: what this changes — tasks affected, architecture implications, scope changes
- **Project**: infer from context. Ask if unclear.

If context or who is unclear, ask. Decisions without context are useless later.

## Write to decisions.md

Add a new entry to the project's `decisions.md`:

```markdown
## YYYY-MM-DD — [short title of decision]
- **Context**: [what prompted this]
- **Decision**: [what was decided]
- **Who**: [people involved]
- **Impact**: [what this changes]
```

## Check for side effects

After logging, check if the decision affects:
- Any tasks in `my-work.md` — update status, add notes, mark as superseded
- Any delegated work — does someone need to know about this change?
- Any previous decisions — does this supersede an earlier one? If so, add a note: `**SUPERSEDES**: [date] [old decision title]`

Tell the user about any side effects found.

## Confirm

Show the decision as logged. Ask: "Anything to add or correct?"
