---
name: daily-review
description: Morning check-in, evening reflection, and weekly review routines. Helps maintain journaling habit and task awareness.
---

# Daily Review System

USE WHEN the user mentions:
- "morning routine", "start my day", "morning check-in"
- "evening routine", "end of day", "wrap up", "evening reflection"
- "weekly review", "week in review", "how was my week"

## How It Works

This skill works closely with:
- **Kanban skill** — to check and update tasks
- **Memory system** — to update learnings and work status
- **Daily folder** (`05_daily/`) — to store journal entries

## Routing

Determine which routine to run:
1. Check current time — if before noon, suggest morning; after 5pm, suggest evening
2. If the user explicitly requests a type, use that
3. If weekly is requested, run the weekly review

## Templates

Templates for each routine are in `.claude/skills/daily-review/templates/`:
- `morning.md` — Morning check-in template
- `evening.md` — Evening reflection template
- `weekly.md` — Weekly review template

## File Naming Convention

- Morning: `05_daily/YYYY-MM-DD Morning.md`
- Evening: `05_daily/YYYY-MM-DD Evening.md`
- Weekly: `05_daily/YYYY-MM-DD Weekly Review.md`

## Cross-References

After each review:
- Update the Kanban board with any new or completed tasks
- Update `.claude/context/memory/work_status.md` with session summary
- Add any new learnings to `.claude/context/memory/learnings.md`
- Link to relevant projects using [[wiki links]]
