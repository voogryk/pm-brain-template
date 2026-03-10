# PM Brain

A file-based personal PM assistant powered by [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

You talk to Claude in your terminal. It reads and writes markdown files to track your work, your team, your decisions — everything a lead engineer juggles daily. Every conversation starts fresh; the files **are** the memory.

## Who is this for?

Engineers who also wear PM/BA/lead hats and need help keeping track of:
- Their own tasks across multiple projects
- Work delegated to team members
- Bugs, decisions, follow-ups
- Daily standups and weekly reviews

## How it works

1. Clone this repo
2. Open it with Claude Code (`claude` in the terminal)
3. Say "start day" — Claude reads all your files, builds a morning briefing, and helps you plan
4. Throughout the day — dump things into inbox, delegate tasks, log bugs, capture decisions
5. Say "finish day" — Claude walks you through a wrap-up, writes a daily log, commits everything

Claude has no memory between sessions. The markdown files are the single source of truth. Claude reads them at the start, writes updates during the session, and commits at the end.

## Getting started

```bash
git clone https://github.com/voogryk/pm-brain-template.git pm-brain
cd pm-brain
claude
```

Then say "start day" or create your first project with `/new-project`.

### Customize

- **Language**: Edit the `## Language` section in `CLAUDE.md` to set your preferred language
- **Projects**: Use `/new-project my-app` to scaffold a new project with all standard files
- **People**: People files are auto-created when you delegate tasks, or copy `people/_template.md`
- **Repos**: Add sibling repo paths to `.claude/rules/{project}.md` so Claude can check git logs and PRs

## File structure

```
pm-brain/
├── CLAUDE.md                      # Main instructions for Claude
├── inbox.md                       # Quick capture — dump anything here
├── standup.md                     # Daily standup prep
├── weekly.md                      # Weekly review template
├── daily/                         # Auto-generated daily session logs
├── people/
│   └── _template.md               # Template for new person files
├── projects/                      # Your projects live here (use /new-project)
└── .claude/
    ├── rules/                     # Project-specific context (auto-loads by path)
    ├── skills/                    # Claude Code slash commands
    │   ├── start-day/             # /start-day — morning kickoff
    │   ├── finish-day/            # /finish-day — end of day wrap-up
    │   ├── finish-week/           # /finish-week — weekly review + archive
    │   ├── delegate/              # /delegate — assign work to someone
    │   ├── bug/                   # /bug — log a bug
    │   ├── decide/                # /decide — log a decision
    │   └── new-project/           # /new-project — scaffold a new project
    └── settings.local.json        # Permission presets
```

## Skills (slash commands)

| Command | What it does |
|---|---|
| `/start-day` | Morning routine: pull repos, read all files, build briefing, plan the day |
| `/finish-day` | End of day: review tasks one by one, capture new info, write daily log, commit |
| `/finish-week` | Weekly review: summarize the week, surface concerns, archive completed items |
| `/delegate` | Assign a task to someone — updates `delegated.md` + `people/{name}.md` |
| `/bug` | Log a bug with severity — writes to project's `bugs.md` |
| `/decide` | Capture a decision with context — writes to `decisions.md`, checks side effects |
| `/new-project` | Scaffold a new project folder with all standard files + rule |

## Tips

- **Be messy with inbox.** Just say "remember X" or "add this to inbox" — Claude will triage it later
- **Delegate naturally.** Say "tell John to fix the login bug by Friday" — Claude updates all the right files
- **Trust the daily log.** `daily/YYYY-MM-DD.md` files are your permanent history. Future sessions read them to know what happened
- **Weekly cleanup is automatic.** `/finish-week` archives all completed items so your active files stay clean
- **Project rules are powerful.** Put repo paths, tech stack, Jira keys in `.claude/rules/{project}.md` — they auto-load when Claude touches that project's files

## License

MIT
