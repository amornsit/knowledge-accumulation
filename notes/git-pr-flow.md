---
title: Git PR flow
created: 2026-07-09
tags: [Git, GitHub, workflow, programming]
source:
---

# Git PR flow

## Notes

The standard pull request workflow used day to day. Never commit straight to
`main` — instead: branch → commit → push → open PR → review → merge → clean up.
The PR is the "please review and merge my work" request, plus the place where
discussion, CI, and approval happen.

## Key points

### The loop at a glance

```bash
git switch main && git pull
git switch -c feature/x
# work + commit
git push -u origin feature/x
gh pr create --fill
gh pr checks          # wait for green, address feedback
gh pr merge --squash --delete-branch
git switch main && git pull
```

### Step by step

| step | command | why |
| --- | --- | --- |
| 1. Start from latest main | git switch main && git pull | base branch on current code, fewer conflicts |
| 2. Create feature branch | git switch -c feature/add-login | one branch = one focused unit of work |
| 3. Commit in logical chunks | git add . && git commit -m "..." | small commits make review + revert easier |
| 4. Push the branch | git push -u origin feature/add-login | -u sets upstream, later just git push |
| 5. Open the PR | gh pr create --fill | describe what changed and why, link issue (Closes #42) |
| 6. Review cycle | gh pr checks | address feedback with more commits, then push |
| 7. Keep branch current | git rebase main | resolve conflicts on your branch, not at merge |
| 8. Merge | gh pr merge --squash --delete-branch | once approved and CI green |
| 9. Clean up | git switch main && git pull && git branch -d feature/add-login | remove merged branch |

### Merge strategies

| strategy | result | when |
| --- | --- | --- |
| squash | all PR commits become one commit on main | most common — clean, linear history |
| rebase | commits replayed individually onto main | keep each commit, no merge bubble |
| merge commit | keeps branch history + adds merge commit | preserving context of a big feature |

### Keeping a branch current when main moved

```bash
git switch main && git pull
git switch feature/add-login
git rebase main               # or: git merge main
git push --force-with-lease   # only needed after a rebase
```

### Principles

- Small PRs get reviewed faster and merge cleaner than big ones.
- Never force-push shared branches — --force-with-lease on your own PR branch is
  fine, but not on main.
- Let CI be the gatekeeper — don't merge red builds.
- Address review feedback with new commits on the same branch; the PR updates
  automatically on push.
