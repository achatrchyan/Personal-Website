# Pre-publish checklist

## Done — ready to publish

- [x] **Deploy workflow.** `.github/workflows/deploy.yml` builds on every push to
      `master` and publishes to GitHub Pages. It checks out the theme submodule and
      takes the base URL from Pages itself, so no `baseURL` edit is needed and it
      works at a user page *or* a project subpath. Verified against a simulated
      subpath build: no link, stylesheet or image resolves to the wrong place.
- [x] **Blog hidden.** The `Blog` menu entry is commented out in `config.toml` and
      `content/physicsblog/_index.md` carries `draft: true` with a `cascade`, so the
      whole section (including the stray Armenian `_index.hy.md`) is excluded from
      the build. The files stay in the repo; `hugo server -D` still shows them.
- [x] **Meta descriptions.** Site-wide fallback in `config.toml`, plus a
      `description:` on Research, Music and Birdwatching.
- [x] **Figure weight.** Research figures are re-encoded to WebP at build time —
      that page went from ~1.4 MB of images to ~280 kB. Sources stay PNG.
- [x] **Empty taxonomy pages** (`/tags/`, `/categories/`) no longer generated.
- [x] **README.md** for anyone landing on the repo.
- [x] Research blurbs rewritten in your own words; no `DRAFT` markers left.

## Before you push — needs you

- [ ] **Make the repo public** (free GitHub Pages needs it), then
      **Settings → Pages → Build and deployment → Source: "GitHub Actions"**.
      Nothing else to configure.
- [ ] **Pick the repo name**, which decides the address:
      - `achatrchyan.github.io` → site at `https://achatrchyan.github.io/`
      - any other name (e.g. `Personal-Website`) → `https://achatrchyan.github.io/Personal-Website/`
      Both work as-is. Renaming later is easy but changes the URL.
- [ ] **Commit everything.** The working tree has a lot of uncommitted work, and
      `public/` was untracked from git earlier — that deletion is staged and needs
      committing too.

## Worth doing, not blocking

- [ ] **Double-check two bird IDs** in `content/birds/_index.md`: the Mallard
      (eclipse-plumage ducks are genuinely ambiguous) and the Young Stonechat
      (could be a whinchat).
- [ ] **Decide on a custom domain** if you'd rather not use a github.io address.
      Needs a `static/CNAME` file and a DNS record.
- [ ] Add an email or contact line somewhere — there's currently no way for a
      visitor to reach you except the social icons.

## Optional tidying

- [ ] Delete `layouts/index.html` — dead file, `layouts/home.html` is what renders.
- [ ] Delete the unused physicsblog episode-list block in `layouts/_default/section.html`
      (duplicated in `layouts/physicsblog/list.html`, which wins for that section).
- [ ] `content/physicsblog/episode_1/my-first-post.md` never renders — it sits inside
      a leaf bundle, so Hugo treats it as a resource, not a page. Sort out when you
      come back to the blog.
- [ ] Re-sync the three forked theme files after any ananke submodule update:
      `layouts/baseof.html`, `layouts/_partials/social/follow.html`,
      `layouts/_partials/site-navigation.html`. Each has a header comment explaining why.
