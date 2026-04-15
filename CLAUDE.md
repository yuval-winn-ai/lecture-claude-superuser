# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What This Is

A reveal.js lecture slide deck for a talk titled **"Working with Claude Code as a Super User"**. The main theme is **working in parallel on many Claude sessions simultaneously** — every feature and demo in the talk serves this throughput goal.

The presenter (Yuval) delivers this live with three screens: laptop, Android phone, and the slideshow. The phone screen is used to show notifications arriving from Claude sessions.

## Commands

```bash
npm start          # Serve slides at http://localhost:3000
```

Slides are a single `index.html` using reveal.js from `node_modules`. No build step required.

## Lecture Intent & Scope

### The Core Message

Developers already use Claude Code, but one session at a time. This talk shows them how to run 5+ sessions in parallel, safely, with full visibility — going from ~3 PRs/day to 10+.

### Topics Covered (in section order)

1. **Where to run Claude Code** — Warp (best for parallel, native notifications, tab scripting), VS Code Extension (best for single-task), Web (best for background/long tasks), iTerm2/Terminal.app tradeoffs
2. **Keyboard shortcuts** — `Esc` (cancel), `Ctrl+G` (external editor), `Ctrl+O` (transcript viewer), `Ctrl+T` (todos), `Shift+Tab` (cycle mode), `⌥P` (model picker), `⌥O` (fast mode), `Ctrl+B` (background task). Press `?` for full reference.
3. **Plan mode** — `"defaultMode": "plan"` in settings.json makes Claude wait for approval before editing — the safety net for parallel sessions
4. **Updating Claude's config** — when Claude doesn't follow instructions more than once, update `~/.claude/settings.json` or `~/.claude/CLAUDE.md` instead of repeating yourself
5. **File references** — `@filename` sends entire file (wasteful); prefer "read lines 40-80 of src/foo.ts" for surgical context use
6. **Context window** — short focused parallel sessions beat one mega-session hitting context limits. Reference: https://code.claude.com/docs/en/context-window
7. **"Interview me" pattern** — tell Claude to interview you before coding or before proposing workarounds
8. **CLAUDE.md and Skills** — persistent instructions (global + per-project) and skills encode multi-step workflows so sessions are self-sufficient with zero re-explaining
9. **Hooks & notifications** — `notify.sh` + `focus-warp-tab.sh`: clicking a macOS notification lands you on the exact Warp tab where Claude finished. Hooks config: `~/.claude/settings.json`. The PostToolUse hook guards code quality when you can't watch every session.
10. **TypeScript LSP plugin** — Claude checks types as it goes; sessions don't stall on type errors asking for your help
11. **Local MCP servers** — MongoDB (via 1Password `op://`), Google Sheets, Gmail, Claude-in-Chrome. Self-sufficient sessions query their own data.
12. **`/update-jira` skill** — auto-detect ticket from branch → fetch PR via `gh` → Qodo review → backup + update 3 Jira fields. Fire and forget.
13. **CLI-first** — `gh` for GitHub (PRs, issues, checks, CI logs), `gcloud`, `op`. CLIs are scriptable; browsers require copy-paste. Enforce in CLAUDE.md.
14. **Fix PR review comments** — paste PR URL, Claude reads via `gh pr view`, fixes all review comments
15. **Fix failed CI** — paste Actions run URL, Claude reads via `gh run view --log-failed`, fixes the failure
16. **Git worktrees** — `git worktree add ../repo-feature branch` gives each session its own working tree with shared `.git`. No conflicts between parallel Claude sessions on the same repo.
17. **Maintaining order** — branch name = Jira ticket = Warp tab name = session purpose. `git-report.sh` gives bird's-eye view. Dashboard shows live session status.
18. **Claude remote control** — trigger and send prompts to running sessions from another context (phone → laptop)
19. **Claude in Chrome** — `claude-in-chrome` MCP: read console errors, network requests, page content. Claude debugs without you copy-pasting browser output.
20. **Dashboard app** (`~/scripts/claude-dashboard`) — React 19 + Python SSE + watchdog. Real-time view of all active sessions, status (thinking/waiting/idle), per-session notes, Claude todos. Air traffic control for parallel work.
21. **Utility scripts** (from `winn-ai/manual-actions`):
    - `git-report.sh` — multi-repo status: branch, dirty, stash, worktree detection, origin sync
    - `git-reset-repos.sh` — interactive fzf multi-select stash+pull or conditional-pull
    - `deploy-pr.sh` — one-command PR deploy: auto-detect repo, monitor CI, fetch image, k8s rollout, Slack notify

### Demo Prep

See `DEMO-PREP.md` for the full pre-lecture checklist and a demo-to-screen mapping table.

### Slide Structure

The deck is a single `index.html`. Sections are delimited by HTML comments (`<!-- SECTION N: ... -->`). Each section has a numbered divider slide followed by content slides. Speaker notes are in `<aside class="notes">` tags — press `S` in the browser to open presenter view.

Section numbers match the topics list above (Section 1 = Foundations, ..., Section 9 = Closing recipe).

## Key External Files Referenced in the Lecture

| File | Purpose |
|------|---------|
| `~/.claude/settings.json` | Hooks, plugins, permissions, defaultMode |
| `~/.claude/hooks/notify.sh` | Notification hook — terminal-notifier + tab focus |
| `~/.claude/hooks/focus-warp-tab.sh` | Warp tab cycling on notification click |
| `~/.claude/skills/update-jira/SKILL.md` | 7-step Jira update skill |
| `~/.claude/CLAUDE.md` | Global persistent instructions (gh CLI, Jira field IDs) |
| `~/scripts/claude-dashboard/` | Dashboard app (React + Python) |
| `~/winn-ai/manual-actions/scripts/deploy-pr.sh` | PR deployment script |
| `~/winn-ai/manual-actions/git-report.sh` | Multi-repo status reporter |
| `~/winn-ai/manual-actions/git-reset-repos.sh` | Multi-repo reset tool |
