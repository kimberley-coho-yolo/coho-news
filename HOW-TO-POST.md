# How to post a news update

You can do all of this in your web browser on github.com. No software to install.

## Post a new update (about 5 minutes)

1. Open this repository on github.com and click the **`_posts`** folder.
2. Click **Add file → Create new file**.
3. Name the file with the date first, then a short title, joined by dashes:
   `2026-11-23-pilot-group-announced.md`
4. Open `_drafts/example-update.md` in another tab, copy its contents, and paste them in.
5. Change the `title`, `tag` and `summary` at the top (keep the quote marks), then write your update below the `---` line.
6. Click **Commit changes…** → **Commit changes**.
7. Wait about a minute, then refresh the website. The newest post appears at the top.

## Fix a typo in an existing update

Open the file in `_posts`, click the **pencil icon**, make the change, then **Commit changes**.

## Remove an update

Open the file, click **⋯ → Delete file**, then **Commit changes**. (It stays in the history if you need it back.)
Or, to hide it without deleting, add `published: false` on a new line in the top section.

## Markdown cheat sheet

| You type | You get |
|---|---|
| `## Heading` | A section heading |
| `**bold**` | **bold** |
| `- item` | A bullet point |
| `1. item` | A numbered list |
| `[link text](https://example.com)` | A link |
| `> Note` | A highlighted callout |
| A blank line | A new paragraph |

Use the **Preview** tab while editing to check how it looks before you commit.

## Before you publish, check

- Plain language, one main message
- No costs, budgets, supplier names under negotiation, or passwords
- No details of security settings (say *what* staff need to do, not *how* our systems are configured)
- Dates match the Key dates page (update `key-dates.md` if they've moved)

## Change site settings

Edit **`_config.yml`** for the contact email and the question form link.
Edit **`key-dates.md`** to update the timeline.
