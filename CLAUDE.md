# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

A **ProperDocs + MaterialX** static documentation site: a wiki for a culinary program. There is no application code — content lives in Markdown under `docs/`, and the build renders it to a static HTML site. Work here is mostly editing/adding Markdown pages and adjusting navigation.

> [!note] Build driver is ProperDocs, theme is MaterialX
> The site is built with **ProperDocs** — a drop-in continuation of MkDocs 1.x — driven from `properdocs.yml`, using the **`materialx`** theme (a material-compatible fork of `mkdocs-material`). The `mkdocs` library is still installed underneath. Use `properdocs`, not `python -m mkdocs`.

> [!warning] The toolchain lives in WSL (Ubuntu), not Windows
> `properdocs`, `materialx`, and the plugins are installed in a **pipx** venv inside **WSL Ubuntu** (`/home/tklun/.local/share/pipx/venvs/properdocs`). They are NOT on the Windows PATH, and the Windows `python -m properdocs` resolves to a **stale pip env that only has `mkdocs-material`** — building through it fails with `Unrecognised theme name: 'materialx'`. Always drive builds by bridging into WSL:
> ```bash
> wsl.exe -e bash -lic 'cd /mnt/c/users/tklun/documents/projects/culinary-wiki && properdocs build'
> ```
> The `-l` (login) flag is required so `~/.local/bin` (the pipx shim dir) is on PATH.

## Commands

Run everything **inside WSL** (see the toolchain warning above). From a Windows shell, bridge in with `wsl.exe -e bash -lic '...'`; from an Ubuntu shell, drop the wrapper and run `properdocs ...` directly:

```bash
wsl.exe -e bash -lic 'cd /mnt/c/users/tklun/documents/projects/culinary-wiki && properdocs serve'          # Live preview at http://127.0.0.1:8000
wsl.exe -e bash -lic 'cd /mnt/c/users/tklun/documents/projects/culinary-wiki && properdocs build'          # Render static site into ./site
wsl.exe -e bash -lic 'cd /mnt/c/users/tklun/documents/projects/culinary-wiki && properdocs build --strict' # Treat warnings as errors
```

The toolchain is managed with **pipx**, not a `requirements.txt`. If the venv is ever rebuilt, restore the non-default extras:

```bash
pipx install properdocs && pipx inject properdocs materialx mkdocs-exporter   # + the other plugins in properdocs.yml
pipx runpip properdocs run playwright install chromium                        # PDF export needs a headless browser
sudo $(pipx environment --value PIPX_LOCAL_VENVS)/properdocs/bin/python -m playwright install-deps chromium  # OS libs (libnspr4, etc.)
```

## Architecture

- **Navigation is NOT in `properdocs.yml`.** The `awesome-pages` plugin builds the nav from `.pages` files placed in `docs/` directories (the plugin's default filename — the extensionless `.pages`, NOT `.pages.yml`; a `.pages.yml` is silently ignored and the nav falls back to sentence-cased folder names). Edit `docs/.pages` (and any nested `.pages`) to change ordering/titles — do not add a `nav:` block to `properdocs.yml`. Individual page labels come from each file's front-matter `title:`.
- **Section (folder) nav entries have exact syntax rules.** In a `.pages` `nav:`, reference a **page** with `Title: file.md` (e.g. `Home: index.md`), but reference a **folder** as a *bare* list item (`- core`) — `Title: folder` is treated as a link to a nonexistent `folder.md` and renders a broken tab. Give the folder its display name with a `title:` key inside *that folder's own* `.pages`. To make clicking the section/tab open its landing page (not the first child), enable `navigation.indexes` (already on) and list `- index.md` as the **first** item of that folder's `nav:`; it collapses into the section instead of showing as a duplicate row.
- **Search must use the `material/search` plugin, not plain `search`.** materialx reuses mkdocs-material's templates, and the header only renders the search UI when `"material/search" in config.plugins`. The generic `search` plugin (properdocs' built-in) still builds `search_index.json`, so search *works* but the search **bar is invisible** — a silent, confusing failure. Always list `- material/search` in `properdocs.yml`.
- **Content is organized by course**, each a top-level section shown as a navigation tab (`navigation.tabs` feature): `core/` (Core Skills), `food-nutrition/`, `culinary-1/`, `culinary-2/`. `glossary.md` and `index.md` sit at the `docs/` root.
- **Section landing pages** are `index.md` files inside each folder.
- **`drafts/*`, `_templates/*`, and `.obsidian/*` are excluded from builds** via the `exclude` plugin. `docs/` is an **Obsidian vault**, so `.obsidian/` must stay excluded — otherwise the editor config leaks into the site *and* its stray stylesheets crash the PDF exporter's post-build step.
- **Dates come from the `document-dates` plugin**, which reads git commit history — a page must be committed for its date to render. `show_author: false` is set so pages show dates but not commit authors (the plugin also supports `show_author: text` for a plain-text author with no link).
- **PDF export via `mkdocs-exporter`.** Each page renders to a downloadable PDF (a "Download as PDF" button appears on the page), produced at build time with a headless Chromium. Because `mkdocs-exporter`'s theme factory hard-matches the theme *name* and would reject `materialx`, the plugin config sets `theme: {name: material}` to force the material handler (safe — materialx is material-compatible). An optional `aggregator` (currently off) can stitch all pages into one combined handbook PDF.
- **PDF rendering is gated behind the `ENABLE_PDF` env var** (`enabled: !ENV [ENABLE_PDF, false]`). It is **off by default** because rendering runs on every `serve`/`build` (incl. each live-reload) and takes ~40s for the full site. Turn it on only when you need PDFs:
  - `ENABLE_PDF=true properdocs build` — full publish build with PDFs.
  - `ENABLE_PDF=true properdocs serve --dirty` — live PDF preview; `--dirty` re-renders only the edited page (the exporter queues a render per rebuilt page, so dirty builds are incremental — no plugin-level cache exists).
- **`--dirty` does NOT rebuild the navigation** — this is the big footgun. Under `serve --dirty`, editing a `.pages` file (reordering/renaming) or adding a page will NOT update the nav; the stale nav tree persists, and newly-added pages can even render with a `None` title. Use plain `properdocs serve` whenever you touch `.pages`, reorder, or add/rename pages. Reserve `--dirty` for content-only edits (and PDF preview) where the structure is stable. Always do a clean `properdocs build` before publishing.

## Authoring conventions

- Callouts use the `callouts` plugin syntax (Obsidian-style `> [!note]` blocks), not raw Material admonitions. The `callouts` plugin only *rewrites* these into `!!! note` admonition syntax — the `admonition` markdown extension (in `markdown_extensions:` in `properdocs.yml`) is what actually renders them. If that extension is removed, callouts silently pass through as literal `!!! note` text instead of erroring.
- Image lightboxes come from `glightbox` automatically — just use standard Markdown images.
- The `macros` plugin is enabled, so `{{ ... }}` in Markdown is treated as a Jinja2 expression; escape literal double braces if you need them as text.
