# Knowledge Accumulation

A personal, growing knowledge base — summaries, atomic notes, and references I want
to keep, recombine, and reuse over time.

## How it's organized

```text
summaries/    Digested articles, books, talks — one source per file
notes/        Atomic notes and TILs — one idea per file, in my own words
references/   Cheatsheets, curated link lists, quick-lookup tables
templates/    Starting templates for new notes
```

## Finding things

- **[INDEX.md](INDEX.md)** — the curated table of contents, grouped by topic. Start here.
- Or browse the folders above.

## Adding a note

1. Copy [`templates/note-template.md`](templates/note-template.md) into the right folder.
2. Follow [`CONVENTIONS.md`](CONVENTIONS.md) for naming and structure.
3. Add a line to [`INDEX.md`](INDEX.md) so it stays discoverable.

## Linting

Markdown style and links are checked automatically — there's no Python or Node
project to set up here, and no `pyproject.toml`.

- **Locally:** install the runner once, then enable the git hook:

  ```sh
  brew install pre-commit        # or: pipx install pre-commit / uv tool install pre-commit
  pre-commit install
  ```

  `markdownlint-cli2` then runs on every commit (in a Node environment `pre-commit`
  manages for you). Run it across everything on demand with `pre-commit run --all-files`.
- **In CI:** [`.github/workflows/lint.yml`](.github/workflows/lint.yml) runs the same
  Markdown lint plus [`lychee`](https://github.com/lycheeverse/lychee) dead-link
  checking on every push and PR.
- **Check links locally (optional):** if you have `lychee` installed
  (`brew install lychee`), run `lychee --config lychee.toml './**/*.md'`.

## License

Original writing here is licensed [CC BY 4.0](LICENSE). Summaries distill
third-party sources, which are cited within each note and remain the property of
their original authors.
