You are preserving permanent learnings into the memory system. Unlike /compress (which saves session-specific context), /preserve saves durable knowledge that should persist indefinitely.

## What Gets Preserved

Things like:
- Project conventions and standards
- Architecture decisions
- Key file paths and workflows
- User preferences that were explicitly stated
- Recurring patterns or rules
- "Always do X" or "Never do Y" instructions

## Step 1: Identify What to Preserve

Ask the user: "What should I remember permanently?"

Or, if the user already stated something (e.g., "remember that I always want..."), proceed directly.

## Step 2: Write to the Right File

| Type of Knowledge | Where to Write |
|-------------------|---------------|
| User preferences, style, habits | `.claude/context/memory/user_preferences.md` |
| Project info, deadlines, details | `.claude/context/memory/user_projects.md` |
| General insights, patterns | `.claude/context/memory/learnings.md` |
| Rules about how I should behave | Root `CLAUDE.md` (under Rules section) |

## Step 3: Auto-Archive Check

After writing, check the file size:

- If **`learnings.md`** exceeds 150 lines → Archive older entries to `.claude/context/memory/archive/`
- If **`user_preferences.md`** exceeds 100 lines → Consider consolidating
- If **`user_projects.md`** has completed projects → Move them to an archive section within the file

Archive format: `.claude/context/memory/archive/[filename]-archive-YYYY-MM.md`

**Protected content** (never archive):
- Current active projects in `user_projects.md`
- Core preferences in `user_preferences.md`
- The most recent 20 learnings in `learnings.md`

## Step 4: Confirm

Tell the user exactly what was saved and where. Quote the text that was added so they can verify accuracy.

## Teaching Loop

If the user corrected you during this session, ask:
"Should I also add a rule to CLAUDE.md so I don't make this mistake again?"

If yes, add the correction as a rule under the Rules section of root `CLAUDE.md`.

This is how the system learns from you over time — every correction becomes a permanent rule.
