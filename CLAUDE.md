# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A **ProperDocs + Material** static documentation site: a wiki for a culinary program. There is no application code — content lives in Markdown under `docs/`, and the build renders it to a static HTML site. Work here is mostly editing/adding Markdown pages and adjusting navigation.

> [!note] Build driver is ProperDocs, not MkDocs
> The site is built with **ProperDocs** — a drop-in continuation of MkDocs 1.x — driven from `properdocs.yml`. The `mkdocs` library and the `mkdocs-material` theme are still installed underneath (ProperDocs and the plugins depend on them); ProperDocs just replaces the CLI/build driver. Use `python -m properdocs`, not `python -m mkdocs`.

## Commands

Bare `properdocs` and `pip` are not on PATH in this environment — invoke through the interpreter with `python -m`:

```bash
python -m properdocs serve            # Live-reloading preview at http://127.0.0.1:8000 (use while editing)
python -m properdocs build            # Render the static site into ./site (fails on broken config/plugins)
python -m properdocs build --strict   # Treat warnings (e.g. broken links) as errors
```

Install dependencies from the pinned list before the first build:

```bash
python -m pip install -r requirements.txt
```

## Architecture

- **Navigation is NOT in `properdocs.yml`.** The `awesome-pages` plugin builds the nav from `.pages` files placed in `docs/` directories (the plugin's default filename — the extensionless `.pages`, NOT `.pages.yml`; a `.pages.yml` is silently ignored and the nav falls back to sentence-cased folder names). Edit `docs/.pages` (and any nested `.pages`) to change ordering/titles — do not add a `nav:` block to `properdocs.yml`. Individual page labels come from each file's front-matter `title:`.
- **Section (folder) nav entries have exact syntax rules.** In a `.pages` `nav:`, reference a **page** with `Title: file.md` (e.g. `Home: index.md`), but reference a **folder** as a *bare* list item (`- core`) — `Title: folder` is treated as a link to a nonexistent `folder.md` and renders a broken tab. Give the folder its display name with a `title:` key inside *that folder's own* `.pages`. To make clicking the section/tab open its landing page (not the first child), enable `navigation.indexes` (already on) and list `- index.md` as the **first** item of that folder's `nav:`; it collapses into the section instead of showing as a duplicate row.
- **Content is organized by course**, each a top-level section shown as a navigation tab (`navigation.tabs` feature): `core/` (Core Skills), `food-nutrition/`, `culinary-1/`, `culinary-2/`. `glossary.md` and `index.md` sit at the `docs/` root.
- **Section landing pages** are `index.md` files inside each folder.
- **`drafts/*` is excluded from builds** via the `exclude` plugin — put work-in-progress pages under a `drafts/` folder to keep them out of the published site.
- **Git-dependent build.** The `git-revision-date-localized` plugin reads commit history to stamp page dates, so a page must be committed for its date to render; building a shallow/detached checkout can warn.

## Authoring conventions

- Callouts use the `callouts` plugin syntax (Obsidian-style `> [!note]` blocks), not raw Material admonitions. The `callouts` plugin only *rewrites* these into `!!! note` admonition syntax — the `admonition` markdown extension (in `markdown_extensions:` in `properdocs.yml`) is what actually renders them. If that extension is removed, callouts silently pass through as literal `!!! note` text instead of erroring.
- Image lightboxes come from `glightbox` automatically — just use standard Markdown images.
- The `macros` plugin is enabled, so `{{ ... }}` in Markdown is treated as a Jinja2 expression; escape literal double braces if you need them as text.
