---
type: reference
title: Quick Start Guide
date: 2026-02-23
---

# Personal Assistant — Quick Start Guide

Get your AI-powered second brain running in under 10 minutes.

## What Is This?

This is an Obsidian vault that doubles as a personal AI assistant. It uses Claude Code (or Claude Co-Work) to:
- Manage your tasks with TaskNotes
- Process meeting transcripts and extract action items
- Run daily routines (morning check-in, evening reflection, weekly review)
- Remember your preferences, projects, and thinking patterns
- Write in your voice across different formats (YouTube scripts, emails, blog posts, etc.)
- Track goals from 3-year vision down to daily tasks

Everything is stored as markdown files on your local machine. You own it completely.

## Step 1: Install Obsidian

Download Obsidian from [obsidian.md](https://obsidian.md/) — it's free.

## Step 2: Open This Vault

1. Open Obsidian
2. Click "Open folder as vault"
3. Select this `personal-assistant` folder
4. When prompted, click "Trust author and enable plugins"

You should see the vault folders in the sidebar:
- Inbox, Thinking, Projects, Meetings, Daily, Reference, Archive, Goals

## Step 3: Install Community Plugins

The vault is pre-configured to use these plugins:
1. **TaskNotes** — Task management system
2. **Dataview** — Database-like queries on your notes

To install them:
1. Go to Settings (gear icon) → Community Plugins
2. Turn off "Restricted mode"
3. Click "Browse" and search for "TaskNotes" — Install and Enable
4. Search for "Dataview" — Install and Enable

## Step 4: Launch Claude Code

Open your terminal, navigate to this folder, and run:

```bash
cd /path/to/personal-assistant
claude
```

## Step 5: Run Setup

Type `/setup` in Claude Code. The assistant will:
1. Ask you about yourself, your work, and what you want to track
2. Build a personalized vault structure based on your answers
3. Configure memory files with your preferences
4. Set up your initial tasks in TaskNotes

## Step 6: Start Using It

Now just talk naturally:

| You Say | What Happens |
|---------|--------------|
| "Add a task: finish the proposal by Friday" | Creates a task in TaskNotes |
| "Morning routine" or `/daily-review` | Runs your morning check-in |
| [Paste a meeting transcript] | Processes it, extracts action items, saves to meetings folder |
| "Write a YouTube script about X" | Uses your YouTube script output style |
| "Draft an email to Sarah about the project update" | Uses your email output style |
| "What tasks are overdue?" | Checks your TaskNotes |
| "What did we discuss in last week's standup?" | Searches your meeting notes |

## Core Commands

| Command | What It Does |
|---------|-------------|
| `/setup` | Personalize your vault (run this first) |
| `/resume` | Start a session — loads recent context, pending tasks, work status |
| `/compress` | Save session before ending — creates searchable session log |
| `/preserve` | Save permanent learnings to memory |
| `/daily-review` | Morning check-in, evening reflection, or weekly review |

### Recommended Daily Workflow

```
Morning:  /resume → /daily-review → work
          (loads context, plans your day)

During:   Just talk naturally
          (Claude manages files, tasks, memory)

Evening:  /compress
          (saves everything for next time)
```

## How Memory Works

The assistant remembers you across sessions through three mechanisms:

1. **Automatic** — Hooks inject memory reminders every turn + block stopping if memory wasn't updated
2. **Session Logs** — `/compress` saves structured session summaries that `/resume` can search
3. **Permanent Memory** — `/preserve` saves durable knowledge that persists indefinitely

### The Teaching Loop

When you correct Claude, it offers to save the correction as a permanent rule. Over time, the system learns exactly how you like things done. Every mistake only happens once.

## The Goal Cascade

```
3-Year Vision → Yearly Goals → Projects → Monthly Goals → Weekly Review → Daily Tasks
```

Goals live in `Goals/`. Projects link to goals. Tasks link to projects. During weekly reviews, Claude flags goals that have no active project (they're drifting). Nothing falls through the cracks.

## Privacy & Safety

**Important**: When you use Claude Code, your vault content is sent to Anthropic's servers for processing.

### What to know:
- Claude reads files to understand context — it may access notes you didn't explicitly mention
- Your data is processed by Anthropic's API (subject to their data policy)
- Claude Code is not suitable for highly sensitive data (medical records, passwords, financial credentials)

### How to protect yourself:
- **`.claudeignore`** — We've included this file. Add paths to any folders/files Claude should never read
- **Keep secrets outside the vault** — Passwords, API keys, credentials should live elsewhere
- **Review changes** — Always check what Claude creates or modifies before committing
- **Git version control** — Initialize git (`git init`) and commit regularly. Claude is good about this, but you should verify
- **Uncomment private folders** — In `.claudeignore`, uncomment lines for `private/`, `journal/`, `finance/`, etc. if you use them

### For maximum privacy:
- Keep truly private thoughts in a separate vault that Claude can't access
- Use `.claudeignore` aggressively
- Consider offline/local LLM options if privacy is paramount (this is evolving rapidly)

## For Claude Co-Work Users

If you're using Claude Co-Work instead of Claude Code:
1. Open Co-Work and grant access to this folder
2. The CLAUDE.md file will guide the assistant
3. **You get**: File reading/writing, output styles, vault organization
4. **You don't get**: Hooks (auto-memory), slash commands, bash execution, MCP integrations
5. **Workaround**: Manually tell Claude to "check my memory files" and "update my work status" at start/end of sessions

## Folder Reference

| Folder | Purpose |
|--------|---------|
| `Inbox` | Quick capture — drop anything here |
| `Thinking` | Your ideas, synthesis, thinking patterns |
| `Projects` | Active project folders |
| `Meetings` | Meeting transcripts (by type: standups, client calls, 1:1s) |
| `Daily` | Daily journals and check-ins |
| `Reference` | External knowledge, tools, this guide |
| `Archive` | Completed or inactive content |
| `Goals` | Vision, yearly goals, monthly goals |

## Tips

- **Consistency > Perfection**: A 2-minute morning check-in is better than skipping
- **Wiki links**: Use `[[double brackets]]` to link notes together — Claude does this automatically
- **Ask Claude**: Not sure where something goes? Just ask. Claude knows the vault structure
- **Memory is automatic**: Hooks force memory updates every conversation turn (Claude Code only)
- **Teach, don't repeat**: When you correct Claude, tell it to save the correction. It won't make the same mistake twice
- **Start simple**: Use `/resume`, `/compress`, and `/daily-review` first. Add complexity as needed
- **Version control**: Run `git init` and ask Claude to commit after changes. Mistakes become reversible
- **Customizable**: Add your own output styles, skills, and folder structures as needed
- **Reduce friction, not add it**: If a workflow feels like work, simplify it. The goal is less attention, not more tools
