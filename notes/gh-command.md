---
title: gh command
created: 2026-07-09
tags: [github, git, programming]
---

# gh command

## Notes

`gh` is GitHub's official command-line tool. It does the GitHub-side things
that plain `git` can't — pull requests, issues, CI checks, releases — without
leaving the terminal. Think: `git` manages commits, `gh` manages GitHub.

### Setup & auth

| command | what it does |
| --- | --- |
| gh auth login | sign in to GitHub (one-time, opens browser) |
| gh auth status | check who you're logged in as |
| gh repo clone [owner/repo] | clone a repo by name (no full URL needed) |
| gh repo create | create a new GitHub repo from the current folder |
| gh repo view --web | open the current repo in the browser |

### Pull requests — the everyday flow

| command | what it does |
| --- | --- |
| gh pr create | open a PR from the current branch (prompts for title/body) |
| gh pr create --fill | open a PR, auto-filling title/body from commits |
| gh pr status | show PRs relevant to you (yours, needing review) |
| gh pr view | show the current branch's PR details |
| gh pr view --web | open the PR in the browser |
| gh pr checks | show CI check results (pass / fail / pending) |
| gh pr merge [n] --squash --delete-branch | merge PR #n as one commit and delete the branch |
| gh pr list | list open PRs in the repo |
| gh pr checkout [n] | check out someone else's PR branch locally |

### Issues

| command | what it does |
| --- | --- |
| gh issue create | open a new issue (prompts for title/body) |
| gh issue list | list open issues |
| gh issue view [n] | show issue #n |
| gh issue close [n] | close issue #n |

### CI / Actions

| command | what it does |
| --- | --- |
| gh run list | list recent workflow runs |
| gh run view [id] | show details of a run |
| gh run watch | follow a running workflow live until it finishes |

### Handy

| command | what it does |
| --- | --- |
| gh browse | open the current repo/file on github.com |
| gh release create [tag] | publish a new release |
| gh gist create [file] | share a file as a gist |
