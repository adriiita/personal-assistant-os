---
type: guide
folder: 04_tasks
---

# Tasks

Task management hub. Two options available:

## Option 1: Kanban Board (Default — No Setup Required)

Your Kanban board lives at `boards/main-kanban.md`. Open it in Obsidian with the Kanban plugin installed to see a visual board.

### Lanes
- **Not Started** — Tasks you haven't begun
- **In Progress** — Tasks you're actively working on
- **Done** — Completed tasks

### Managing Tasks via Claude
Just tell Claude:
- "Add a task: Write blog post, due Friday"
- "Move 'write blog post' to In Progress"
- "What tasks are overdue?"
- "Mark 'write blog post' as done"

## Option 2: TaskNotes Plugin (Optional Power-User Upgrade)

If you install the TaskNotes Obsidian plugin:
- Individual task files with rich metadata
- HTTP API for programmatic access
- Built-in Pomodoro timer, time tracking, calendar views

See `.claude/skills/tasknotes/SKILL.md` for setup instructions.

## Tips
- Review your board during morning and evening routines (`/daily-review`)
- Archive completed tasks to `07_archive/` during weekly reviews
- Tag tasks with `#project-name` to link them to projects
