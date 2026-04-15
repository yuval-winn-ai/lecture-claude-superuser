# Demo Preparation Checklist

Run through this checklist 30 minutes before the lecture.

## Environment

- [ ] Warp terminal open with at least 6 tabs, clearly named
- [ ] Dashboard app running (`python3 ~/scripts/claude-dashboard/server/claude_dashboard.py`)
- [ ] Dashboard open in browser tab
- [ ] Chrome open with a staging app that has a known console error (for §5.4 demo)
- [ ] Phone connected, screen sharing ready
- [ ] `terminal-notifier` installed and tested: `terminal-notifier -title Test -message "works?" -sound Glass`

## Git Worktrees

- [ ] Pre-create 2-3 worktrees so `git-report.sh` output shows them:
  ```bash
  cd ~/repos/your-repo
  git worktree add ../your-repo-demo-1 some-branch-1
  git worktree add ../your-repo-demo-2 some-branch-2
  ```
- [ ] Verify: `git worktree list` shows them

## PR & CI Demos

- [ ] Identify a real PR with 2-3 review comments for the "Fix PR review" demo (§6.2)
- [ ] Identify a failed GitHub Actions run URL for the "Fix failed action" demo (§6.3)
- [ ] Have a Jira ticket with a linked PR for the `/update-jira` demo (§3.3)

## Claude Sessions to Pre-Start

For the signature notification demo (§4.5), prepare 3 Warp tabs:
- [ ] **Tab A** — named clearly (e.g., "WINN-1234 fix-login")
- [ ] **Tab B** — named clearly (e.g., "WINN-1235 new-api")  
- [ ] **Tab C** — named clearly (e.g., "WINN-1236 refactor")

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
| §1.12 | Keyboard shortcuts (Esc, Ctrl+G, Ctrl+O, Shift+Tab) | Laptop |
| §1.13 | Plan mode — start task, review plan | Laptop |
| §2.3 | Context window — interactive docs visualizer | Chrome |
| §2.4 | "Interview me" — new session | Laptop |
| §3.3 | `/update-jira` on real PR (canonical skill demo) | Laptop |
| §4.5 | **Signature:** 3 tabs, notification → tab focus | Laptop + Phone |
| §5.1 | TypeScript LSP catching type error | Laptop |
| §5.2 | MongoDB MCP query | Laptop |
| §5.4 | Chrome console → fix bug | Chrome + Laptop |
| §6.2 | Fix PR review comments | Laptop |
| §6.3 | Fix failed CI action | Laptop |
| §7.1 | Create worktree, parallel Claude sessions | Laptop |
| §7.2 | Dashboard walkthrough | Dashboard (browser) |
| §7.3 | `git-report.sh` output, `deploy-pr` alias | Laptop |
| §7.4 | Remote control trigger | Laptop + Phone |
