# Account landing pages

Static, single-file landing pages for account outreach. No build step, no
dependencies — each page is one self-contained `index.html`.

```
/index.html              Nominal × Anduril
/innoflight/index.html   Nominal × Innoflight
/innoflight/og.png       Link-preview image for the Innoflight page
```

## Publishing

GitHub Pages serves the repo directly:

**Settings → Pages → Source: Deploy from a branch → `main` / `/ (root)`**

URLs follow the directory layout:

| Page | URL |
| --- | --- |
| Anduril | `https://spencerrusso-hub.github.io/anduril-landing-page/` |
| Innoflight | `https://spencerrusso-hub.github.io/anduril-landing-page/innoflight/` |

A page is live within a minute or two of merging to `main`.

## Adding a new account page

1. Copy `innoflight/index.html` to `<account>/index.html`.
2. Update the `<title>`, meta description, and the `og:*` / `twitter:*` tags —
   including the absolute `og:image` and `canonical` URLs, which must point at
   the new directory.
3. Swap the accent color (`#2b7cd3` / `#4a9eea` on the Innoflight page) for the
   account's brand color.
4. Regenerate the link-preview image (see below).

## Link previews

`og.png` is what renders when the link is pasted into email, Slack, or LinkedIn.
It must be 1200×630 and referenced by absolute URL. Regenerate it by editing the
card markup and re-running the screenshot:

```bash
npx playwright screenshot --viewport-size=1200,630 og-card.html og.png
```

## Notes

- Each page carries `<meta name="robots" content="noindex, nofollow">` so account
  pages don't surface in search. Delete that line to make a page publicly
  indexable — link previews keep working either way.
- Tabs are deep-linkable: `…/innoflight/#apps` opens Applications Engineering
  directly, so a single team can be sent straight to their own section.
