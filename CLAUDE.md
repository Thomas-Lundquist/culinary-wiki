# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A **MkDocs + Material** static documentation site: a wiki for a culinary program. There is no application code — content lives in Markdown under `docs/`, and the build renders it to a static HTML site. Work here is mostly editing/adding Markdown pages and adjusting navigation.

## Commands

```bash
mkdocs serve     # Live-reloading preview at http://127.0.0.1:8000 (use this while editing)
mkdocs build     # Render the static site into ./site (fails on broken config/plugins)
mkdocs build --strict   # Treat warnings (e.g. broken links) as errors
```

There is no `requirements.txt`. `mkdocs.yml` enables several third-party plugins that must be installed first, or every command fails at startup:

```bash
pip install mkdocs-material mkdocs-awesome-pages-plugin mkdocs-macros-plugin \
  mkdocs-callouts mkdocs-glightbox mkdocs-git-revision-date-localized-plugin \
  mkdocs-exclude mkdocs-print-site-plugin
```

## Architecture

- **Navigation is NOT in `mkdocs.yml`.** The `awesome-pages` plugin builds the nav from `.pages.yml` files placed in `docs/` directories. Edit `docs/.pages.yml` (and any nested `.pages.yml`) to change ordering/titles — do not add a `nav:` block to `mkdocs.yml`.
- **Content is organized by course**, each a top-level section shown as a navigation tab (`navigation.tabs` feature): `core/` (Core Skills), `food-nutrition/`, `culinary-1/`, `culinary-2/`. `glossary.md` and `index.md` sit at the `docs/` root.
- **Section landing pages** are `index.md` files inside each folder.
- **`drafts/*` is excluded from builds** via the `exclude` plugin — put work-in-progress pages under a `drafts/` folder to keep them out of the published site.
- **Git-dependent build.** The `git-revision-date-localized` plugin reads commit history to stamp page dates, so a page must be committed for its date to render; building a shallow/detached checkout can warn.

## Authoring conventions

- Callouts use the `callouts` plugin syntax (Obsidian-style `> [!note]` blocks), not raw Material admonitions.
- Image lightboxes come from `glightbox` automatically — just use standard Markdown images.
- The `macros` plugin is enabled, so `{{ ... }}` in Markdown is treated as a Jinja2 expression; escape literal double braces if you need them as text.
