---
name: tasknotes
description: HTTP API-based task management using the TaskNotes Obsidian plugin. Optional upgrade — requires TaskNotes plugin running on port 8090.
---

# TaskNotes Integration (Optional)

USE WHEN the user has the TaskNotes Obsidian plugin installed and running, AND they prefer API-based task management over the Kanban board.

## Prerequisites

- TaskNotes plugin installed in Obsidian (v4.3.0+)
- HTTP API enabled in plugin settings (port 8090)
- Plugin data config: `httpApi.enabled: true, httpApi.port: 8090`

## API Reference

Base URL: `http://127.0.0.1:8090/api`

### List All Tasks
```bash
curl -s "http://127.0.0.1:8090/api/tasks"
```

### List Tasks by Status
```bash
curl -s "http://127.0.0.1:8090/api/tasks?status=open"
curl -s "http://127.0.0.1:8090/api/tasks?status=in-progress"
curl -s "http://127.0.0.1:8090/api/tasks?status=done"
```

### Create a Task
```bash
curl -s -X POST "http://127.0.0.1:8090/api/tasks" \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Task name",
    "status": "open",
    "priority": "normal",
    "due": "2026-03-15",
    "projects": ["Project Name"]
  }'
```

### Update a Task
```bash
curl -s -X PUT "http://127.0.0.1:8090/api/tasks/Tasks/task-name.md" \
  -H "Content-Type: application/json" \
  -d '{"status": "in-progress"}'
```

### Delete a Task
```bash
curl -s -X DELETE "http://127.0.0.1:8090/api/tasks/Tasks/task-name.md"
```

### Get Available Options
```bash
curl -s "http://127.0.0.1:8090/api/options"
```

## Task Statuses
- `open` — Not started
- `in-progress` — Currently working on
- `done` — Completed

## Task Priorities
- `none` — No priority set
- `low` — Low priority
- `normal` — Default priority
- `high` — High priority

## When to Use TaskNotes vs Kanban

| Feature | Kanban (Default) | TaskNotes |
|---------|-----------------|-----------|
| Setup required | None | Plugin + HTTP API |
| Data format | Pure markdown | Individual task files |
| Visual board | Obsidian Kanban plugin | TaskNotes built-in views |
| API access | File editing | HTTP REST API |
| Dependencies | None | TaskNotes plugin running |
| Best for | Simple task tracking | Complex project management |

## Detecting TaskNotes

Before using this skill, check if the API is running:
```bash
curl -s --max-time 2 "http://127.0.0.1:8090/api/tasks" > /dev/null 2>&1 && echo "TaskNotes is running" || echo "TaskNotes not available — use Kanban instead"
```

If TaskNotes is not running, fall back to the Kanban skill.
