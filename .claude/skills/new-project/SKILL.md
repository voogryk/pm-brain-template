---
name: new-project
description: Create a new project with standard file structure. Use when the user wants to track a new project.
argument-hint: "[project-name]"
disable-model-invocation: true
---

# Create New Project

Scaffold a new project folder with standard PM Brain files.

## 1. Get project info

From `$ARGUMENTS`, get the project name (lowercase, hyphenated). If not provided, ask.

Then ask:
- "What is this project? One sentence description."
- "Any specific repos, tech stack, or tools to note?"
- "Any people already involved?"

## 2. Create project structure

```
projects/{project-name}/
├── my-work.md
├── delegated.md
├── bugs.md
├── decisions.md
└── ideas/
```

### my-work.md
```markdown
# {Project Name} — My Work

## In Progress

## Up Next

## Blocked / Waiting

## Backlog
```

### delegated.md
```markdown
# {Project Name} — Delegated Work

Tasks assigned to or expected from others. Follow up if overdue.

## Active

## Waiting for Response

## Completed (Recent)
```

### bugs.md
```markdown
# {Project Name} — Bugs

Known bugs and issues.

## Open

## Resolved
```

### decisions.md
```markdown
# {Project Name} — Decisions Log

Important decisions for future reference. "Why did we do that?"
```

## 3. Create project rule

Create `.claude/rules/{project-name}.md` with frontmatter:

```yaml
---
paths:
  - "projects/{project-name}/**"
---

# {Project Name} — Project Rules

{description from user}

## Project Files

- `my-work.md` — tasks for this project
- `delegated.md` — delegated work tracking
- `bugs.md` — known bugs and issues
- `decisions.md` — decisions log
- `ideas/` — project ideas
```

Add any repos, tech stack, or tools info the user provided.

## 4. Update CLAUDE.md

Add the new project to the "Current Projects" list in `CLAUDE.md`.

## 5. Update people files

If the user mentioned people, add this project to their `**Projects**:` field.

## 6. Confirm

Show the created structure and ask if anything needs to be adjusted.
