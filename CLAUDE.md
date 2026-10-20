# CLAUDE.md

Project-level instructions for Claude Code, loaded at the start of every session in this folder. Four sections, four jobs: a compressed map of the workspace, the conventions Claude follows here, what Claude can already do here, and a log of what has been tried.

## Workspace map

A Claude Code plugin (`meetings`, v1.0.0) that turns meeting transcripts into assets: summaries, action items, decision logs, reports and follow-up emails, agendas, and consultative proposals. Pure Markdown, with no build step or dependencies.

- `.claude-plugin/plugin.json`: plugin manifest (name, version, description).
- `.claude-plugin/marketplace.json`: the single-plugin marketplace `trishussey-meetings` (source `./`).
- `skills/<name>/SKILL.md`: one skill per folder: `meeting-summary`, `action-items`, `strategic-alignment`, `meeting-deliverables`, `agenda-maker`, `consultant-proposal`, and `meetings-manager` (runs the full workflow phase by phase).
- `README.md`: user-facing skill table and install instructions.
- Skills chain on purpose: `meeting-deliverables` and `agenda-maker` expect analysis from `meeting-summary` / `strategic-alignment`, or run it first.

Fixed locations:
- `active/` — everything generated: scratch scripts, exports, intermediate output. Subfolders per task. Short-lived files go in `active/.tmp/`.
- `.env` — every key and credential. Referenced by variable name only.
- `.claude/` — project-local skills, agents, and settings.
- `AGENTS.md` — same content as this file, for non-Claude agents.

## Preferences & conventions

- Never write to the project root. Generated files, one-off scripts, and scratch output go in `active/` or a subfolder of it.
- Run commands yourself rather than handing them back to be pasted. The only exception is a command that needs credentials only the user holds.
- Never read, print, or echo the contents of `.env`. Refer to secrets by variable name. Never commit `.env`.
- Before installing a package you have not used in this project before, confirm it exists, is the intended package (not a near-miss name), and has a real history.
- After finishing any development pass, spawn a fresh QA reviewer with no project context (`tickety-boo:qa-reviewer`) before reporting done. Fix its blockers and should-fix items and re-run it; stop when only nits remain or after three rounds, and report anything still open.
- When you make a mistake, append one dated line to **Lab notes** below describing what not to try next time, written for a future instance of you.
- Whenever this file changes, `AGENTS.md` must match it (symlink, or re-sync). In a Claude Code plugin repo (`.claude-plugin/plugin.json` exists), keep it a plain copy, not a symlink: the plugin directory validator skips symlinks.
- The transcript is the only source of truth in every skill: missing owners become **Unassigned** and missing deadlines **TBD**. Keep that rule consistent when you edit or add skills.
- When you add, rename, or remove a skill, update the README table. If the plugin description changes, update `plugin.json` and `marketplace.json` together.
- Test changes locally with `claude --plugin-dir .` before calling them done.

## Capabilities

- `claude --plugin-dir .`: loads this plugin locally for testing.
- No scripts, tests, or deploy targets yet. Distribution is via GitHub marketplace install (see README).
- Default autonomy: for a well-scoped task, plan it, build it, validate it, and report back. Do not check in mid-task on implementation details that do not change the request's scope.

## Lab notes: what not to do

- 2026-10-19: (empty — first entry goes here)
