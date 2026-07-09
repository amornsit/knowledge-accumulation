---
title: Git command
created: 2026-09-07
tags: [Git, programming]
---

# Git command

## Notes

### Setup & config

| command | what it does |
| --- | --- |
| git init | start new repo |
| git clone [url] | copy a remote repo locally |
| git config --global user.name "..." | set your name |
| git config --global user.email "..." | set your email |

### Everyday workflow

| command | what it does |
| --- | --- |
| git status | show changed/staged/ untracked files |
| git add [file] | stage changes for commit |
| git commit -m "msg" | commit stage changes |
| git commit -am "msg" | stage tracked files + commit in one step |
| git diff | show unstaged changes |
| git diff --staged | show staged changes |
| git log --oneline --graph | compact commit history |

### Branching

| command | what it does |
| --- | --- |
| git branch | list branch |
| git switch [name] | switch to a branch |
| git switch -c [name] | create and switch to a new branch |
| git merge [name] | merge a branch into current |
| git rebase [name] | replay your comits on top of another branch |
| git branch -d [name] | delete a branch |

### Remote and syncing

| command | what it does |
| --- | --- |
| git remote -v | list remotes |
| git fetch | download remote changes (don't merge) |
| git pull | fetch + merge remote into currenct branch |
| git push | upload commits to remote |
| git push -u origin [branch] | push + set upstream (first push of a branch) |

### Undo and fix mistakes

| command | what it does |
| --- | --- |
| git restore [file] | discard unstaged changes to a file |
| git restore --staged [file] | unstage a file (keep changes) |
| git reset --soft HEAD~1 | undo last commit, keep changes staged |
| git reset --hard HEAD~1 | undo last commit and discard changes |
| git revert [commit] | make a new commit that undoes an old one (safe fore shared history) |
| git commit --amend | edit the last commit (message or contents) |
| git stash / git stash pop | shelved changes temmporarily, then restore |

### Inspecting

| command | what it does |
| --- | --- |
| git show [commit] | show a commit's changes |
| git blame [file] | see who last changed each line |
| git reflog | history of where HEAD has been (great for recovering "lost" commit) |
