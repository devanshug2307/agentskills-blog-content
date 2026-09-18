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


## Depth standard (user requirement 2026-09-17)

Blog posts on agentskills.codes must match the analytical depth of agentpedia.codes
flagship posts. A launch/guide post ships with ALL of the following:

- **2,500+ words** of body prose (not counting code blocks)
- A **claim-by-claim evidence table** when the topic makes claims (✅ verified / ⚠️ peaks / ❌ vendor-only)
- **Named independent tests** with their actual numbers (who ran it, what they measured, what it means)
- **Vendor-vs-verified separation** — every load-bearing claim graded, fine print included
- **Caveats section** — methodology biases, demo caveats, unanswered questions
- **Practical verdict** — use it if / be skeptical if / watch for
- **FAQ** (6+ questions) and **dated Sources** list
- Embedded first-party media: `{% x %}` post embeds (the actual launch thread), `{% youtube %}` demos

Do not ship a "doorway" post. The blog funnels into the skill registry, but thin
posts lose rankings — depth is the ranking asset. Reference example:
`posts/typesafe-jev/article.mdoc` (deep) vs the pre-expansion draft (too thin).

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
