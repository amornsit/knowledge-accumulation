# Conventions

Rules for adding notes so the collection stays consistent and searchable as it grows.

## Where things go

| Folder | Contents |
|--------|----------|
| `summaries/` | Digested articles, books, talks, videos — one source per file. |
| `notes/` | Atomic notes and TILs — one idea per file, written in your own words. |
| `references/` | Cheatsheets, curated link lists, quick-lookup tables. |
| `templates/` | Starting templates to copy when creating a new note. |

## File naming

- Lowercase, hyphen-separated (kebab-case): `red-green-tdd.md`.
- Descriptive and specific. Prefer `postgres-index-types.md` over `postgres.md`.
- No dates in filenames — Git tracks history. (Use frontmatter `created` if you want a date.)
- Summaries may end in `-summary` to signal they distill an external source.

## Note structure

- Start every note with an `# H1 Title`.
- Copy `templates/note-template.md` as a starting point.
- For summaries, **always cite the source** (title + link) at the top and bottom.
- Keep one clear topic per file. If a note grows two topics, split it.
- Use tags in frontmatter (`tags: [agents, testing]`) to group across folders.

## Keeping the index current

- After adding a note, add a line to `INDEX.md` under the right topic heading.
- The index is curated by hand — it is the fastest way to find things.

## Attribution

- Summaries distill third-party work. Cite the original author and link.
- Original writing here is CC BY 4.0 (see `LICENSE`).
