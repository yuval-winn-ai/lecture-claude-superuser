# Demo Preparation Checklist

Run through this checklist 30 minutes before the lecture.

## Environment

- [ ] Warp terminal open with at least 6 tabs, clearly named
- [ ] Dashboard app running (`python3 ~/scripts/claude-dashboard/server/claude_dashboard.py`)
- [ ] Dashboard open in browser tab
- [ ] Chrome open with a staging app that has a known console error (for §4.4 demo)
- [ ] Docs tab pre-loaded: `https://docs.anthropic.com/en/docs/claude-code/context-window` (for §1.3 demo)
- [ ] Phone connected, screen sharing ready
- [ ] `terminal-notifier` installed and tested: `terminal-notifier -title Test -message "works?" -sound Glass`

## Git Worktrees

- [ ] Pre-create 2-3 worktrees so `git-report.sh` and the §6.1 demo show them:
  ```bash
  cd ~/repos/your-repo
  git worktree add ../your-repo-demo-1 some-branch-1
  git worktree add ../your-repo-demo-2 some-branch-2
  ```
- [ ] Verify: `git worktree list` shows them

## PR & CI Demos

- [ ] Identify a real PR with 2-3 review comments for the "Fix PR review" demo (§5.2)
- [ ] Identify a failed GitHub Actions run URL for the "Fix failed action" demo (§5.3)
- [ ] Have a Jira ticket with a linked PR for the `/update-jira` demo (§3.3); open the Jira ticket in a browser tab on the side screen

## Parallel Sessions for the Dashboard Demo

For the Dashboard demo (§6.3), have 3-5 Warp tabs running Claude sessions with meaningful names and varied states (thinking / waiting / idle). Convention: branch name = Jira ticket = Warp tab name.

- [ ] **Tab A** — e.g., "WINN-1234 fix-login" (mid-task, should show *thinking*)
- [ ] **Tab B** — e.g., "WINN-1235 new-api" (paused at a permission prompt → *waiting*)
- [ ] **Tab C** — e.g., "WINN-1236 refactor" (completed / *idle*)

## Slides

- [ ] Start slide server: `cd ~/work-projects/lecture-claude-superuser && npm start`
- [ ] Open slides in browser, test navigation (arrow keys)
- [ ] Test presenter mode: press `S` in slides to open speaker notes window
- [ ] Verify code highlighting renders correctly

## Scripts

- [ ] Verify `git-report.sh` runs: `~/winn-ai/manual-actions/git-report.sh`
- [ ] Verify `deploy-pr` alias exists in shell: `type deploy-pr`

## Demo Flow Quick Reference

| Section | Demo | Screen |
|---------|------|--------|
| §1.3 | Context window — interactive docs visualizer | Chrome |
| §1.4 | "Interview me" — new session | Laptop |
| §2.14 | Essential shortcuts (Esc, Ctrl+G, Ctrl+O, Shift+Tab, ⌥P, ⌥O, Ctrl+B) | Laptop |
| §2.15 | Slash commands — `/`, `/new`, `/resume`, `/usage`, `/chrome` | Laptop |
| §2.16 | Plan mode — start task, review plan | Laptop |
| §3.3 | `/update-jira` on real PR (canonical skill demo) | Laptop + Jira browser |
| §4.1 | TypeScript LSP catching type error | Laptop |
| §4.2 | MongoDB MCP query | Laptop |
| §4.4 | Chrome console → fix bug | Chrome + Laptop |
| §5.2 | Fix PR review comments | Laptop |
| §5.3 | Fix failed CI action | Laptop |
| §5.4 | `git-report.sh` output, `deploy-pr` alias | Laptop |
| §6.1 | Create worktree, parallel Claude sessions | Laptop |
| §6.3 | Dashboard walkthrough | Dashboard (browser) |
| §6.4 | Remote control trigger | Laptop + Phone |
