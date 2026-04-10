# personal-website setup & runbook

Updated 2026-04-10 to work with Hugo 0.160.1.

## Running locally

From RStudio (the way you normally work):

```r
setwd("~/Dropbox/Personal/personal-website")
library(blogdown)
blogdown:::serve_site()     # starts Hugo on http://127.0.0.1:4321
```

Or from the shell:

```bash
cd ~/Dropbox/Personal/personal-website
hugo server                 # http://127.0.0.1:1313
hugo --gc                   # production build into ./public
```

## Hugo version

Pinned to **0.160.1** in three places — keep them in sync if you ever bump it:

- `.Rprofile` → `options(blogdown.hugo.version = "0.160.1")`
- `netlify.toml` → `HUGO_VERSION = '0.160.1'`
- `/usr/local/bin/hugo` (the binary blogdown actually uses)

## What changed during the Hugo upgrade

Newer Hugo is stricter than 0.89.2 was. Fixes applied to `config.yaml`:

- YAML booleans: `yes`/`no` → `true`/`false` everywhere (new Hugo's YAML parser rejects the old 1.1 spelling).
- `privacy.twitter` → `privacy.x` (Twitter key was removed in Hugo v0.141).
- Removed `preserveTaxonomyNames` (removed from Hugo long ago; was a no-op).
- Added `markup.goldmark.parser.attribute.block: false` — belt-and-braces; attribute parsing was causing trouble on some old content.

Content fix:

- `content/projects/2021-06-19-notes-on-latex/index.md` — removed R Markdown–style code-fence attributes (` ```{latex, eval = FALSE} ` → ` ```latex `). Four occurrences in one file. The original is backed up at `~/Desktop/deleted by clawd/notes-on-latex.index.md.orig`.

Theme override:

- `layouts/partials/head.html` — drops the dead `_internal/google_analytics_async.html` reference (the standard `google_analytics.html` still works).

## Threads icon

Added a Threads entry to `params.social` in `config.yaml`. The theme uses Font Awesome 5.15.1 which predates the Threads glyph, so `layouts/partials/shared/social-links.html` overrides the theme's social rendering and inlines an SVG from `cdn.simpleicons.org` when `icon: threads`. Same pattern in the blog repo.

## Files backed up during migration

Everything I touched that had a prior version was copied to `~/Desktop/deleted by clawd/` before editing:

- `personal-website.config.yaml.orig`
- `personal-website.Rprofile.orig`
- `notes-on-latex.index.md.orig`

Nothing was deleted.
