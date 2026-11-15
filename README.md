# Personal website

Source for my personal site: research, music and wildlife photography.

Built with [Hugo](https://gohugo.io/) (extended) on top of the
[Ananke](https://github.com/theNewDynamic/gohugo-theme-ananke) theme, which is
included as a git submodule.

## Running it locally

```bash
git clone --recurse-submodules <this repo>
cd Personal-Website
hugo server          # http://localhost:1313
hugo server -D       # also shows drafts (the blog section is a draft)
```

If you cloned without `--recurse-submodules`, the theme will be missing:

```bash
git submodule update --init --recursive
```

## How it is deployed

Every push to `master` triggers `.github/workflows/deploy.yml`, which builds the
site and publishes it to GitHub Pages. The build output (`public/`) is
deliberately **not** committed — the workflow is the only thing that produces
the live site. The base URL comes from GitHub Pages itself, so the same
configuration works whether the site is served from a user page or from a
project subpath.

## Layout of the repository

| Path | What's in it |
| --- | --- |
| `config.toml` | Site configuration, menu, colours |
| `content/` | Page content and the images belonging to each page |
| `layouts/` | Templates — per-section layouts, plus a few theme overrides |
| `assets/css/custom.css` | The dark theme; the whole palette is five CSS variables at the top |
| `themes/ananke/` | Theme, as a submodule — don't edit in place |
| `PUBLISH-CHECKLIST.md` | Running list of things to settle before/around going live |

Three files under `layouts/` are deliberate forks of theme files
(`baseof.html`, `_partials/social/follow.html`, `_partials/site-navigation.html`).
Each carries a comment saying why, and they need re-syncing if the theme
submodule is updated.

## Content

Most pages are driven by front matter rather than markup, so adding a photo, a
paper or a research theme means editing a list in the relevant `_index.md`
rather than touching a template. The comments in those files explain the fields.

## A note on the photographs

The bird and wildlife photographs in `content/` are my own. The code here is
free to borrow; please don't reuse the photos without asking.
