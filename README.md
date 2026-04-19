# Working with Claude Code as a Super User

A [reveal.js](https://revealjs.com/) slide deck for a live talk on running **many Claude Code sessions in parallel** — going from one-session-at-a-time to 5+ concurrent sessions with full visibility.

The core message: developers already use Claude Code, but most run it one session at a time. This deck walks through the setup, knowledge-encoding, tooling, and workflow patterns that make parallel operation safe and productive (~3 PRs/day → 10+).

## Running the slides

```bash
npm install
npm start
```

Then open <http://localhost:3000>. No build step — the deck is a single `index.html` that loads reveal.js from `vendor/`.

### Presenter controls

- `S` — open presenter view with speaker notes
- `F` — fullscreen
- `?` — show all reveal.js shortcuts
- `Esc` — slide overview

## Layout

| Path | Purpose |
|------|---------|
| `index.html` | The entire deck — sections delimited by `<!-- SECTION N: ... -->` comments |
| `vendor/reveal.js/` | Vendored reveal.js assets (so the deck can be served from GitHub Pages) |
| `CLAUDE.md` | Guidance for Claude Code when editing the deck — section map, intent, and load-bearing slides |
| `DEMO-PREP.md` | Pre-lecture checklist and demo-to-screen mapping |

## Section map

1. **§0 Opening Hook** — the problem: one session at a time
2. **§1 Efficiency & Focus** — token economics, `@filename` refs, context window
3. **§2 Setup & Foundations** — where to run Claude, CWD pitfalls, multi-repo with `--add-dir`
4. **§3 Encoding Knowledge** — settings, `CLAUDE.md`, Skills, hooks
5. **§4 Power Tools** — LSP, MCP servers, Claude-in-Chrome, Qodo
6. **§5 CLI-First Workflows** — `gh` for PRs and CI, `/update-jira`
7. **§6 Parallel Mastery** — git worktrees, the [Claude Sessions Dashboard](https://github.com/yuval-yssak/claude-dashboard), remote control
8. **§7 Closing** — the daily parallel recipe

## Editing

Speaker notes live in `<aside class="notes">` blocks inside each `<section>`. When adding or reordering slides, preserve the section comment markers so `CLAUDE.md`'s section map stays accurate.
