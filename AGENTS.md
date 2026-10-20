# CLAUDE.md

Project-level instructions for Claude Code, loaded at the start of every session in this folder. Four sections, four jobs: a compressed map of the workspace, the conventions Claude follows here, what Claude can already do here, and a log of what has been tried.

## Workspace map

A Claude Code plugin (`meetings-to-actions`, v1.0.0, MIT licensed) that turns meeting transcripts into assets: summaries, action items, decision logs, reports and follow-up emails, agendas, and consultative proposals. Pure Markdown, with no build step or dependencies.

- `.claude-plugin/plugin.json`: plugin manifest (name, version, description).
- `.claude-plugin/marketplace.json`: the single-plugin marketplace `trishussey-meetings` (source `./`).
- `.claude-plugin/` also holds the listing icon (calendar with a pen, 1024 px square PNG) at the default location the directory picks up. Read the first Lab note before mentioning it anywhere.
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
- The transcript is the only source of truth in every skill: missing owners become **Unassigned** and missing deadlines **TBD**. Keep that rule consistent when you edit or add skills. The deliberate exception is `consultant-proposal`, which adds labeled inferences and its own recommendations; don't remove it.
- Action-item tables use exactly **Action Item | Owner | Deadline | Notes** in every skill. `meetings-manager` restates the other skills' phases inline rather than calling them, so any change to a phase skill must be mirrored there.
- When you add, rename, or remove a skill, update the README table. If the plugin description changes, update `plugin.json` and `marketplace.json` together.
- Test changes locally with `claude --plugin-dir .` before calling them done.

## Capabilities

- `claude --plugin-dir .`: loads this plugin locally for testing.
- No scripts, tests, or deploy targets yet. Distribution is via GitHub marketplace install (see README).
- Default autonomy: for a well-scoped task, plan it, build it, validate it, and report back. Do not check in mid-task on implementation details that do not change the request's scope.

## Lab notes: what not to do

- 2026-10-19: Never write the path or filename of an image or font file in any Markdown file (CLAUDE.md, AGENTS.md, README, SKILL.md). The directory validator treats it as a possible "run this file" reference (UNREAD_ASSET_REFERENCED) and puts the whole plugin on a policy hold. The icon at its default location needs no mention anywhere.
- 2026-10-19: The plugin directory validator skips symlinks and flags them. Keep AGENTS.md a plain copy.
- 2026-10-19: Shell download-and-run patterns (piping a fetched script into a shell) in README are flagged as an install-time risk. Install instructions stay as `/plugin` commands and `claude --plugin-dir .`.
- 2026-10-19: A plugin name within one or two characters of an existing directory listing goes on a policy hold for review. Check the name against the directory before submitting.
- 2026-10-19: CLAUDE.md at the plugin root gets a warning that it isn't loaded as plugin context. That's expected, because it's for developing the repo, not for users. Anything users need goes in a skill.
