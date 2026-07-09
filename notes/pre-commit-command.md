---
title: pre-commit command
created: 2026-07-09
tags: [pre-commit, git, programming]
---

# pre-commit command

## Notes

`pre-commit` is a framework for managing **Git hooks** — checks (linters, formatters,
fixers) that run automatically before each commit and block it if something fails. It is a
**CLI tool you install and run**, not a library you import. Each hook runs in its own
isolated environment that pre-commit manages, so you don't install every underlying tool
yourself. Config lives in a `.pre-commit-config.yaml` at the repo root.

## Key points

### Install & enable

Install the runner once (any one of these), then enable it per-repo:

| command | what it does |
| --- | --- |
| brew install pre-commit | install the runner (macOS) |
| uv tool install pre-commit | install as an isolated global tool |
| pipx install pre-commit | install as an isolated global tool |
| pre-commit install | wire the hooks into `.git/hooks/` (run once per repo) |

After `pre-commit install`, every `git commit` runs the configured hooks on your **staged** files.

### Everyday commands

| command | what it does |
| --- | --- |
| pre-commit run | run hooks against staged files (what a commit triggers) |
| pre-commit run --all-files | run hooks against the whole repo (first-time cleanup / CI) |
| pre-commit run [hook-id] | run a single hook, e.g. `pre-commit run markdownlint-cli2` |
| pre-commit autoupdate | bump each repo's `rev:` to its latest release |
| pre-commit uninstall | remove the git hook |
| git commit --no-verify | bypass hooks for one commit (use sparingly; `-n` for short) |

### Config (.pre-commit-config.yaml)

```yaml
repos:
  - repo: https://github.com/DavidAnson/markdownlint-cli2  # where the hook lives
    rev: v0.23.0                                           # pinned version (reproducible)
    hooks:
      - id: markdownlint-cli2                               # which hook to run from that repo
        args: [--fix]                                       # optional extra flags
```

- `repos:` — a list; each entry is a source of hooks.
- `rev:` — the pinned tag/commit of that source. Pin it for reproducibility; `autoupdate` bumps it.
- `hooks:` → `id:` — selects a specific hook the source provides. `args:` passes flags to it.

### This repo's setup

The `.pre-commit-config.yaml` here runs three hooks (see also `.markdownlint-cli2.jsonc`):

```yaml
minimum_pre_commit_version: "3.5.0"
repos:
  - repo: https://github.com/DavidAnson/markdownlint-cli2
    rev: v0.23.0
    hooks:
      - id: markdownlint-cli2
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v6.0.0
    hooks:
      - id: end-of-file-fixer
      - id: trailing-whitespace
        args: [--markdown-linebreak-ext=md]
      - id: check-yaml
```

- **markdownlint-cli2** lints every `*.md` file. It runs **offline** via a Node environment
  that pre-commit manages — you do not install Node or markdownlint yourself.
- **end-of-file-fixer** ensures files end in a single newline; **trailing-whitespace** strips
  trailing spaces (the `--markdown-linebreak-ext=md` arg keeps Markdown's two-space line breaks);
  **check-yaml** validates YAML syntax.
- Link checking (lychee) is **not** a hook here — it runs in CI (`.github/workflows/lint.yml`).

### Gotchas

- Only **staged** files are checked by default — use `--all-files` for a full sweep and in CI.
- Auto-fixing hooks (whitespace, EOF, `--fix`) **modify files and abort the commit** — re-stage
  the fixes (`git add`) and commit again.
- Pin `rev:` to a specific version for reproducibility; run `pre-commit autoupdate` when ready.
- Don't rely on `--no-verify` to skip checks permanently — run the same hooks in CI so a local
  bypass still gets caught.
