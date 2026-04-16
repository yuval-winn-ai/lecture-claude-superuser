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

The deck has **8 sections** (Section 0 opener + §1–§7). Each section below maps to one `<!-- SECTION N: ... -->` block in `index.html`.

**§0 Opening Hook** — title, "The Problem" (one session at a time), roadmap.

**§1 Efficiency & Focus** *(prerequisite for parallelism — must come before §6)* — `@filename` vs line-range file references, how the VSCode extension sends a lightweight pointer (not the full file), token economics (usage limits, attention dilution, forced compaction, cache busting, stall risk), context window visualizer (`docs.anthropic.com/en/docs/claude-code/context-window`), "interview me" pattern for both specs and avoiding workarounds. Placed first to establish *why* tokens matter before §2 argues *where* you launch Claude.

**§2 Setup & Foundations** *(intentionally deep — see note below)* — where to run (Warp/Terminal.app/VSCode/iTerm tradeoffs), the "1 Claude = 1 project root" rule, systems that silently fail under wrong CWD (CLAUDE.md, settings.json, .mcp.json, skills, auto-memory, Glob scope, git, Bash blast radius), the VSCode parent-folder trap and fixes, multi-repo with `--add-dir` (anchor primary + extend scope), picking the primary + orienting Claude, cross-repo guardrails, when *not* to go multi-repo + umbrella folder pattern, keyboard shortcuts (`Esc`, `Ctrl+G`, `Ctrl+O`, `Ctrl+T`, `Shift+Tab`, `⌥P`, `⌥O`, `Ctrl+B`), plan mode as default.

**§3 Encoding Knowledge** *(write it down once — every session already knows)* — updating Claude's settings (`~/.claude/settings.json`, `~/.claude/CLAUDE.md`, `.claude/settings.json`, `/update-config`), global + project CLAUDE.md with real examples (gh enforcement, Jira field IDs), Skills as multi-step recipes with **`/update-jira` as THE canonical example** — 7-step breakdown shown in §3.3 and **nowhere else** in the deck, PostToolUse hook for automated self-QA.

**§4 Power Tools** — TypeScript LSP plugin (sessions that type-check themselves don't stall), local MCP servers (MongoDB, Google Sheets, Gmail, Claude-in-Chrome), MongoDB via 1Password `op://`, Claude-in-Chrome MCP (read page/console/network), Qodo PR bot (`/review`, `/agentic_review`, `/ask`).

**§5 CLI-First Workflows** — enforce "always use `gh`" in CLAUDE.md, fix PR review comments from a URL (`gh pr view`), fix failed CI from an Actions run URL (`gh run view --log-failed`). `/update-jira` closes the loop — **named, not re-explained** (it's fully covered in §3.3).

**§6 Parallel Mastery** *(the payoff — everything before sets this up)* — git worktrees (separate checkout, shared `.git`; branch name = Jira ticket = Warp tab name), Claude Sessions Dashboard (`~/scripts/claude-dashboard`, React 19 + Python SSE + watchdog), utility scripts (`git-report.sh`, `git-reset-repos.sh`, `deploy-pr.sh`), Claude remote control (trigger sessions from phone/script/cron).

**§7 Closing** — the daily parallel recipe (9 steps), before/after (3 PRs/day → 10+), Q&A.

### Why §2 is long (intentional — do not compress further without explicit permission)

The CWD / VSCode-parent-folder / cross-repo material in §2 is **intentionally ~11 slides deep**. This is a contested topic in the audience: many devs default to launching Claude from a parent folder in VSCode out of habit. The lecture uses this section to argue that working correctly with Claude matters — and specifically that a real terminal (**Warp** or iTerm2) is the better default for parallel work.

Load-bearing slides in the argument:
- **§2.3 "Why This Matters"** — explicit runway framing the deep-dive as contested territory
- **§2.4 "Everything Keys Off the Working Directory"** — the authoritative table enumerating every system that silently fails under wrong CWD (merged from two near-identical tables in the old deck)
- **§2.5 "The VSCode Parent-Folder Trap"** — carries the Warp-as-better-default pitch ("VSCode as viewer, Warp for Claude — scales best to many parallel sessions")
- **§2.6 "The Silent Failure Mode"** — symptoms the audience will recognize from their own experience

Do not trim this section further. Merge near-duplicate content where genuinely redundant, but preserve the argument's depth.

### Demo Prep

See `DEMO-PREP.md` for the full pre-lecture checklist and a demo-to-screen mapping table.

### Slide Structure

The deck is a single `index.html`. Sections are delimited by HTML comments (`<!-- SECTION N: ... -->`). Each section has a numbered divider slide followed by content slides. Speaker notes are in `<aside class="notes">` tags — press `S` in the browser to open presenter view.

Section numbers match the topics list above: §1 Efficiency & Focus, §2 Setup & Foundations, §3 Encoding Knowledge, §4 Power Tools, §5 CLI-First Workflows, §6 Parallel Mastery, §7 Closing.

## Key External Files Referenced in the Lecture

| File | Purpose |
|------|---------|
| `~/.claude/settings.json` | Hooks, plugins, permissions, defaultMode |
| `~/.claude/skills/update-jira/SKILL.md` | 7-step Jira update skill |
| `~/.claude/CLAUDE.md` | Global persistent instructions (gh CLI, Jira field IDs) |
| `~/scripts/claude-dashboard/` | Dashboard app (React + Python) |
| `~/winn-ai/manual-actions/scripts/deploy-pr.sh` | PR deployment script |
| `~/winn-ai/manual-actions/git-report.sh` | Multi-repo status reporter |
| `~/winn-ai/manual-actions/git-reset-repos.sh` | Multi-repo reset tool |
