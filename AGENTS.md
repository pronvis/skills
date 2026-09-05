# Global rules

## Cross-repo references

Shorthand issue/PR references only resolve inside the current repository. When referencing an issue or PR in another repo, use the full URL, not `repo#N`.

- Wrong (from the `frontend` repo): `openapi#71`
- Right: `https://github.com/<owner>/openapi/issues/71`

Applies everywhere the reference is rendered by GitHub: issue and PR bodies, comments, and commit messages.

## Markdown links

Every reference in a Markdown file carries a real target: a URL for anything on the web, a repo-relative path for another Markdown file. Bracket text with no target renders as literal brackets and leads nowhere.

- Wrong: `[openapi#73]`, ``[`typescript-best-practices`]``
- Right: `[openapi#73](https://github.com/Inkflockteam/openapi/issues/73)`, ``[`typescript-best-practices`](skills/typescript-best-practices/SKILL.md)``

## Chat replies

Apply `skill://unslop` to all chat replies.
