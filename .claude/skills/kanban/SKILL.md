---
name: kanban
description: Manage Kanban boards — create tasks, move between lanes, set due dates, mark complete. Uses the Obsidian Kanban plugin format (pure markdown).
---

# Kanban Board Management

USE WHEN the user wants to:
- Create a new task
- Move a task between lanes (Not Started → In Progress → Done)
- Check what tasks are pending, in progress, or done
- Set or change a due date on a task
- Mark a task as complete
- Create a new Kanban board
- View their task board

## Board Location

Default board: `04_tasks/boards/main-kanban.md`
Additional boards can be created in `04_tasks/boards/`

## Kanban File Format (Obsidian Kanban Plugin)

```markdown
---
kanban-plugin: basic
---

## Not Started
- [ ] Task description @{2026-03-15} #tag
- [ ] Another task #urgent

## In Progress
- [ ] Active task @{2026-03-10}

## Done
**Complete**
- [x] Finished task
- [x] Another finished task
```

### Key Syntax Rules

| Element | Syntax | Example |
|---------|--------|---------|
| Uncomplete task | `- [ ] text` | `- [ ] Write blog post` |
| Complete task | `- [x] text` | `- [x] Write blog post` |
| Due date | `@{YYYY-MM-DD}` | `@{2026-03-15}` |
| Tag | `#tagname` | `#urgent` `#work` `#personal` |
| Lane header | `## Lane Name` | `## In Progress` |
| Done lane marker | `**Complete**` | Must appear after `## Done` heading |

### Operations

**Add a task**: Append `- [ ] task text` under the appropriate `##` lane heading
**Move a task**: Remove the line from one lane and add it to another
**Complete a task**: Change `- [ ]` to `- [x]` and move to `## Done` lane (after `**Complete**`)
**Set due date**: Append ` @{YYYY-MM-DD}` to the task line
**Add a tag**: Append ` #tagname` to the task line
**Delete a task**: Remove the line entirely

### Querying Tasks

To check overdue tasks:
1. Read the board file
2. Find all lines with `@{YYYY-MM-DD}` where the date is before today
3. Report them to the user

To count tasks per lane:
1. Read the board file
2. Count `- [ ]` lines under each `##` heading

## Important Notes

- Always preserve the `kanban-plugin: basic` frontmatter — the Obsidian plugin needs it
- The `**Complete**` marker under `## Done` is required for the plugin to render correctly
- When moving tasks to Done, change `- [ ]` to `- [x]`
- Keep one blank line between the lane header and the first task
- If the user doesn't specify a lane, add new tasks to `## Not Started`
