# agentskills.codes — blog content

Content store for the agentskills.codes blog. This repo is **not** built or deployed:
the site fetches these files at request time (with ISR), so publishing a post here is
live within about a minute — no app rebuild, no redeploy.

## Layout

```
posts/index.json               # array of slugs; the site only reads posts listed here
posts/<slug>/metadata.json
posts/<slug>/article.mdoc      # Markdoc (markdown + custom tags)
images/<slug>/…                # optional local assets referenced from Markdoc
```

## metadata.json

```json
{
  "title": "…",
  "slug": "…",
  "category": "Deep Dives",
  "description": "…",
  "publishedDate": "2026-09-15",
  "updatedDate": "2026-09-20",
  "hero": "https://… or /images/…",
  "author": "Agent Skills",
  "keywords": ["agent skills"],
  "draft": false
}
```

- `title` (required, descriptive, ≲65 chars), `slug` (required, matches the folder),
  `category` (required: `Guides` | `Deep Dives` | `Ecosystem` | `Changelog Watch`),
  `description` (required, ≲155 chars), `publishedDate` (required, ISO date — drives ordering).
- `updatedDate` optional, set only for material updates. `hero` optional image URL.
- `draft: true` means the post is never rendered in production.

## article.mdoc

Standard Markdown plus these tags:

| tag | usage |
|---|---|
| YouTube | `{% youtube id="dQw4w9WgXcQ" title="Demo" /%}` |
| X / Twitter post | `{% x id="1234567890123456789" /%}` |
| Callout | `{% callout type="info" %}` … `{% /callout %}` (info, tip, warning) |
| Figure | `{% figure src="https://…" alt="…" caption="…" /%}` |
| Code | fenced blocks with a language, e.g. a ```ts fence |

Headings get stable kebab-case ids automatically and feed the table of contents.
