---
title: UV command usage
created: 2026-07-09
tags: [uv, programming]
---

# UV command usage

## Notes

### project management

| command | What it does |
| --- | --- |
| uv init [name] | create new project (pyproject.html) |
| uv add [pkg] | add a dependency and update the lockfile |
| uv add --dev [pkg] | Add a dev-only dependency |
| uv remove [pkg] | remove a dependency |
| uv sync | Install deps to match uv.lock (creates .venv) |
| uv lock | resolve and write uv.lock |
| uv run [cmd] | run command inside the project env (auto-syncs first) |
| uv tree | show the dependency tree |

### Running & tools

| command | what it does |
| --- | --- |
| uv run script.py | run script in managed dev |
| uv tool run [tool] or uvx [tool] | run a cli tool in a throwaway env |
| uv tool install [tool] | install a cli tool globally |
