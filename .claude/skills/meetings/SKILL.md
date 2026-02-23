---
name: meetings
description: Process meeting transcripts — extract action items, create summaries, file in correct meeting type folder. Works with manual paste or Fireflies integration.
---

# Meeting Intelligence

USE WHEN the user:
- Pastes a meeting transcript
- Asks to summarize a meeting
- Wants action items from a meeting
- Asks about past meetings or meeting patterns
- Drops a transcript file into `03_meetings/`

## How Meeting Processing Works

### Step 1: Identify Meeting Type

Ask the user or infer from context:
- **Team standup** → save to `03_meetings/team-standups/`
- **Client call** → save to `03_meetings/client-calls/`
- **One-on-one** → save to `03_meetings/one-on-ones/`
- **General** → save to `03_meetings/general/`

### Step 2: Load the Meeting Summary Output Style

Read `.claude/output-styles/meeting-summary.md` and follow its format exactly.

### Step 3: Process the Transcript

From the transcript, extract:
1. **Key decisions** — What was agreed upon?
2. **Action items** — Who is doing what, by when?
3. **Discussion summary** — Brief recap of each topic covered
4. **Open questions** — What was left unresolved?
5. **Follow-up** — Next meeting, items to prepare

### Step 4: Create the Meeting Note

Save as `03_meetings/[type]/YYYY-MM-DD Meeting Title.md` using the template:

```yaml
---
type: meeting
subtype: team-standup | client-call | one-on-one | general
date: YYYY-MM-DD
time: HH:MM
participants: [Person A, Person B]
duration: X minutes
source: manual | fireflies
status: processed
---
```

### Step 5: Create Tasks from Action Items

For each action item extracted:
1. Ask the user if they want to add it to the Kanban board
2. If yes, use the Kanban skill to add it to `04_tasks/boards/main-kanban.md`
3. Include the due date and tag it with the meeting type

### Step 6: Link to Projects

If the meeting relates to a known project (check `.claude/context/memory/user_projects.md`):
- Add a [[wiki link]] to the project in the meeting note
- Update the project file with a reference to this meeting

## Meeting Type Templates

### Team Standup
Focus on: what each person did yesterday, what they're doing today, blockers.
Keep summary very brief — standups are short.

### Client Call
Focus on: client requests, decisions made, next steps, relationship notes.
Check if client exists in `03_meetings/client-calls/` for historical context.

### One-on-One
Focus on: personal development, feedback, goals, action items.
More personal tone — capture the spirit, not just the facts.

### General
Default format. Full meeting summary structure.

## Querying Past Meetings

When the user asks about past meetings:
```bash
# Find meetings with a specific person
grep -rl "Person Name" 03_meetings/

# Find meetings about a topic
grep -rl "topic keyword" 03_meetings/

# List recent meetings
ls -lt 03_meetings/*/
```
