# Demo Preparation Checklist

Run through this checklist 30 minutes before the lecture.

## Environment

- [ ] Warp terminal open with at least 6 tabs, clearly named
- [ ] Dashboard app running (`python3 ~/scripts/claude-dashboard/server/claude_dashboard.py`)
- [ ] Dashboard open in browser tab
- [ ] Chrome open with a staging app that has a known console error (for Section 7B demo)
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

- [ ] Identify a real PR with 2-3 review comments for the "Fix PR review" demo (Section 5B)
- [ ] Identify a failed GitHub Actions run URL for the "Fix failed action" demo (Section 5C)
- [ ] Have a Jira ticket with a linked PR for the `/update-jira` demo (Section 4C)

## Claude Sessions to Pre-Start

For the signature notification demo (Section 3), prepare 3 Warp tabs:
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
| 1B | Keyboard shortcuts (Esc, Ctrl+E) | Laptop |
| 1C | Plan mode — start task, review plan | Laptop |
| 2B | "Interview me" — new session | Laptop |
| 3 | **Signature:** 3 tabs, notification → tab focus | Laptop + Phone |
| 4A | TypeScript LSP catching type error | Laptop |
| 4B | MongoDB MCP query | Laptop |
| 4C | `/update-jira` on real PR | Laptop |
| 5B | Fix PR review comments | Laptop |
| 5C | Fix failed CI action | Laptop |
| 6B | Create worktree, parallel Claude sessions | Laptop |
| 7A | Remote control trigger | Laptop + Phone |
| 7B | Chrome console → fix bug | Laptop (Chrome) |
| 8A | Dashboard walkthrough | Laptop |
| 8B | `git-report.sh` output | Laptop |
