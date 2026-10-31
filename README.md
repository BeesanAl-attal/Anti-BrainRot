# anti-br 🧠

An anti brain-rot mode for AI coding agents. It stops the AI from doing everything for you and teaches you to understand your own code. Works with **Claude** (Claude Code, Claude.ai) and **Cursor**, and the instructions are plain markdown so you can paste them into any other tool.

## Why

When you code with AI agents it's easy to:
- Ask the AI to run basic git commands, so you never learn them
- Re-ask the same question because you never used active recall
- Avoid reading code, so you never build intuition for how projects are structured

`/anti-br` flips the AI from "doer" to "mentor".

## What you get

Every answer comes in short blocks:

| Block | Purpose |
|---|---|
| ⚡ TL;DR | The answer in 1-2 sentences |
| 🧠 Term | The correct technical term, plus what to search |
| 🗂 Where it lives | File tree of your real project |
| 💻 Snippet | Small annotated code (15 lines max) |
| 🔍 Go read this | One file to open, and what to look for |
| ✋ Try it yourself | A 5-minute task |
| 🧩 Quiz | 2-3 questions, answers held back until you reply |

For git and terminal tasks it never runs the command. It shows the command, a breakdown of each flag, how to check it worked, and how to undo it.

## Install

All versions share the same instructions. Pick your tool:

| Tool | Put this file | Invoke with |
|---|---|---|
| Claude Code (all projects) | `skills/anti-br/SKILL.md` → `~/.claude/skills/anti-br/SKILL.md` | `/anti-br` |
| Claude Code (one project) | `.claude/commands/anti-br.md` | `/anti-br` |
| Claude.ai / Claude app | Upload `anti-br-skill.zip` at Settings → Capabilities → Skills | say "use anti-br" or `/anti-br` |
| Cursor (command) | `.cursor/commands/anti-br.md` | `/anti-br` |
| Cursor (rule fallback) | `.cursor/rules/anti-br.mdc` | `@anti-br` |
| Any other tool | Paste the body of `SKILL.md` into its custom instructions | tool-specific |

Menus and folder paths change often, so check each tool's docs if something doesn't show up.

## Usage

```
/anti-br what is a rebase vs a merge
/anti-br tour
/anti-br quiz
/anti-br explain src/routes/auth.ts
/anti-br git undo my last commit
```

| Command | What it does |
|---|---|
| `/anti-br <question>` | Full answer in blocks |
| `/anti-br tour` | Walks you through your project structure |
| `/anti-br quiz` | Quizzes you with no teaching first |
| `/anti-br explain <file>` | Breaks a file into chunks and quizzes you |
| `/anti-br git <task>` | Teaches the git command instead of running it |

## Glossary (active recall)

When you agree, it saves new terms to `.anti-br/glossary.md` in your project. Ask about something you've already learned and it makes you recall it first. Without file access (plain chat), it gives you an entry to copy instead.

## Repo layout

```
anti-br/
├── README.md
├── skills/anti-br/SKILL.md      # Claude skill (source of truth)
├── .claude/commands/anti-br.md  # Claude Code project command
└── .cursor/
    ├── commands/anti-br.md      # Cursor command
    └── rules/anti-br.mdc        # Cursor rule
```
