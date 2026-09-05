# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

**Local development:**
```bash
bundle exec jekyll serve
```
Serves the site at `http://localhost:4000` with live reload.

**Build for production:**
```bash
bundle exec jekyll build
```
Output goes to `_site/` (gitignored).

**Install dependencies:**
```bash
bundle install
```

## Architecture

This is a minimal Jekyll 4.3 static site deployed to GitHub Pages at `madanmohanuk.com`.

**Layout hierarchy:**
- `_layouts/default.html` — root layout: includes `_includes/head.html` and `_includes/sidebar.html`, then renders `{{ content }}`
- `_layouts/page.html` — wraps content in a `<div>`, uses `default` as its layout
- All pages (`index.html`, `books.md`) use `layout: page`

**Includes:**
- `_includes/head.html` — SEO tags (jekyll-seo-tag), Google Analytics (gtag), CSS/font imports, Font Awesome kit
- `_includes/sidebar.html` — fixed dark sidebar with nav links; active state is set by matching `page.name` against filenames (e.g. `index.html`, `books.md`)

**Styling:**
- `assets/css/styles.css` — all custom CSS; sidebar is fixed at 18rem wide on ≥48em viewports, content area uses `margin-left` to offset
- `assets/css/syntax.css` — code syntax highlighting

**Plugins** (all in `_config.yml`):
- `jekyll-feed` — generates `/feed.xml`
- `jekyll-sitemap` — generates `/sitemap.xml`
- `jekyll-seo-tag` — renders `{% seo %}` in head
- `jekyll-gist` — Gist embedding support

**Permalink format:** `/:categories/:title` (set in `_config.yml`).

**Active nav link pattern:** The sidebar uses `{% if page.name == 'filename' %}-active{% endif %}` appended to the CSS class name to switch between `sidebar-nav-item` and `sidebar-nav-item-active`. When adding new pages to the sidebar, follow this same pattern.

**Deployment:** Pushing to `main` triggers GitHub Pages to build and deploy automatically. There is no CI configuration file; deployment is handled entirely by GitHub Pages.
