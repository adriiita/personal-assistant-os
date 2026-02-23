You are running the daily review routine. Determine which type of review to run based on the time of day or the user's request.

## Routing

- **Morning** (before noon, or user says "morning", "start my day"): Run the morning routine
- **Evening** (after 5pm, or user says "evening", "end of day", "wrap up"): Run the evening routine
- **Weekly** (user says "weekly review", "week in review"): Run the weekly routine
- **Unclear**: Ask the user which one they want

## Morning Routine

1. **Review yesterday**: Read the most recent daily note from `Daily/` to see what was planned
2. **Check tasks**: Query TaskNotes API for active tasks — `curl -s "http://127.0.0.1:8080/api/tasks?status=open"` and `curl -s "http://127.0.0.1:8080/api/tasks?status=in-progress"`. What's in progress? What's overdue?
3. **Check projects**: Scan `Projects/` for any deadlines approaching this week
4. **Check-in with the user**: Ask:
   - How are you feeling today? (mood, energy level 1-10)
   - What's your main focus for today?
   - Anything blocking you?
5. **Create daily note**: Save to `Daily/YYYY-MM-DD Morning.md` using this template:

```yaml
---
type: daily-note
subtype: morning
date: YYYY-MM-DD
mood: [user's answer]
energy: [1-10]
focus: [main focus]
---
```

```markdown
# Morning Check-in — YYYY-MM-DD

## How I'm Feeling
[User's mood and energy]

## Today's Focus
[Main priority]

## Tasks for Today
- [ ] [Pulled from TaskNotes or user input]

## Blockers
[Anything blocking progress]
```

6. **Suggest tasks**: Based on energy level and project deadlines, suggest 1-3 tasks. Offer to create them in TaskNotes.
7. **Wrap up**: Brief encouragement. Keep it real, not cheesy.

## Evening Routine

1. **Review today**: Read today's morning note from `Daily/`
2. **Check task progress**: Query TaskNotes API to compare current state vs morning intentions
3. **Ask the user**:
   - What did you accomplish today?
   - One thing you learned?
   - What's your top priority for tomorrow?
4. **Create evening note**: Save to `Daily/YYYY-MM-DD Evening.md`:

```yaml
---
type: daily-note
subtype: evening
date: YYYY-MM-DD
productivity: [1-10]
---
```

```markdown
# Evening Reflection — YYYY-MM-DD

## Accomplished
[What got done]

## Learned
[Key insight from today]

## Tomorrow's Priority
[Top focus for next day]
```

5. **Update TaskNotes**: Mark completed tasks as done via API, carry over in-progress items
6. **Update memory**: Write any new learnings to `.claude/context/memory/learnings.md`

## Weekly Review

1. **Read all daily notes from this week** in `Daily/`
2. **Scan project progress**: Check all projects in `Projects/` for movement
3. **Review completed tasks**: Query TaskNotes for done tasks — celebrate wins
4. **Ask the user**:
   - What was your biggest win this week?
   - What would you do differently?
   - What's your focus for next week?
5. **Create weekly note**: Save to `Daily/YYYY-MM-DD Weekly Review.md`:

```yaml
---
type: daily-note
subtype: weekly-review
date: YYYY-MM-DD
week_number: [W##]
---
```

6. **Plan next week**: Identify top 3 priorities. Offer to create tasks in TaskNotes.
7. **Archive**: Move completed items to `Archive/` if appropriate
8. **Update memory**: Summarize the week in `.claude/context/memory/work_status.md`
