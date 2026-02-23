You are running the interactive vault setup. Your job is to interview the user and build a personalized vault tailored to their life and work.

## How This Works

You will ask questions in stages, going deeper based on the user's answers. You are a thoughtful agent — don't dump all questions at once. Be conversational.

## Stage 1: Who Are You?

Ask about:
- What is your name?
- What do you do? (profession, role, industry)
- What are you currently focused on? (main projects, goals)

## Stage 2: How Do You Work?

Ask about:
- What tools do you use daily? (note-taking, calendar, communication, etc.)
- Do you prefer detailed or concise communication?
- When do you work? (morning person, night owl, specific hours)
- How do you like tasks organized? (lists, kanban boards, calendars)

## Stage 3: What Do You Want to Track?

Present options and ask which are relevant. Recommend based on what you've learned:

- [ ] **Projects** — Active work projects with deadlines and status tracking
- [ ] **Meetings** — Meeting transcripts, action items, summaries
  - Team standups?
  - Client calls?
  - One-on-ones?
  - Other types?
- [ ] **Tasks / Kanban** — Visual task board with lanes (Not Started → In Progress → Done)
- [ ] **Daily Journaling** — Morning check-ins, evening reflections, weekly reviews
- [ ] **Personal Life** — Family, health, fitness, hobbies
- [ ] **Content Creation** — YouTube, blog, social media content pipelines
- [ ] **Client / Relationship Management** — CRM-like contact tracking
- [ ] **Learning / Reference** — Notes from courses, books, research

If the user says "that's enough" or "let's go with this", stop asking and start building.

## Stage 4: Build the Vault

Based on the answers, do ALL of the following:

### 1. Update Memory Files

Write to `.claude/context/memory/user_preferences.md`:
- Communication style preferences
- Tool preferences
- Work schedule
- Task management style

Write to `.claude/context/memory/user_projects.md`:
- All projects mentioned with descriptions and status

### 2. Create Folder Structure

The base folders already exist (00_inbox through 07_archive). Based on what the user wants to track:

- If **Meetings**: Ensure subfolders exist under `03_meetings/` for each meeting type they mentioned
- If **Projects**: Create project folders under `02_projects/` for each active project
- If **Content Creation**: Create content pipeline folders (e.g., `02_projects/youtube/`, `02_projects/blog/`)
- If **Personal Life**: Create relevant subfolders under `01_thinking/` or dedicated folders
- If **Client Management**: Create `02_projects/clients/` with a template

### 3. Create Guide Files

For each active folder, create a `_guide.md` file that explains:
- What goes in this folder
- How files should be named
- What frontmatter to use
- Examples of content

### 4. Create Starter Kanban Board

Create `04_tasks/boards/main-kanban.md` with initial lanes and any tasks the user mentioned:

```markdown
---
kanban-plugin: basic
---

## Not Started

## In Progress

## Done
**Complete**
```

### 5. Update Root CLAUDE.md

If the user mentioned specific projects or preferences that should affect the root CLAUDE.md, update it.

### 6. Confirm Completion

Tell the user:
- What was created
- How to open the vault in Obsidian (just open the `personal-assistant` folder)
- How to start using it ("just talk to me naturally")
- Remind them about key commands: `/daily-review`
- Remind them that memory updates happen automatically

## Guidelines

- Be conversational, not robotic
- Don't ask more than 3 questions at a time
- Recommend things proactively — "Based on what you said, I'd suggest also tracking..."
- If the user seems overwhelmed, simplify and offer to expand later
- Use the user's name once you know it
- Go deeper only if the user is engaged — if they say "keep it simple", respect that
