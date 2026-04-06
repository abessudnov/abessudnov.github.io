# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a personal academic website for Alexey Bessudnov (abessudnov.net), built with [Quarto](https://quarto.org/). It is a static site hosted on GitHub Pages.

## Deployment

**Deploying is just pushing to the `quarto` branch.** GitHub Actions (`.github/workflows/publish.yml`) automatically renders the site and pushes the output to the `gh-pages` branch, which GitHub Pages serves. Never edit the `gh-pages` branch directly.

To preview or build locally:
```bash
quarto preview   # live preview in browser
quarto render    # build to _site/
```

## Structure

All content pages are `.qmd` files at the repository root:

- `index.qmd` — homepage / about (uses Quarto's `trestles` about template)
- `publications.qmd`, `talks.qmd`, `teaching.qmd`, `cv.qmd`, `media.qmd` — content pages

PDF files are stored in three directories and linked with **root-relative paths** (no `../` prefix):
- `filespubs/` — publication PDFs
- `filestalks/` — presentation slide PDFs
- `filesteaching/` — course outlines and materials

Site configuration is in `_quarto.yml`. Visual customisation is in `custom.scss` (overrides the `cosmo` Bootswatch theme).

## Content conventions

- PDF links use the form `[text](filespubs/filename.pdf)` — paths are relative to the root, not to a subdirectory
- Filenames with spaces in `filespubs/` should be renamed with underscores before adding 
- The `index.qmd` front matter contains the author profile block (photo, email, Google Scholar, GitHub links) — edit that block to update contact/social links
- Jekyll-style markup (`{: .notice}`) does not work; use Quarto callouts instead: `::: {.callout-note}` / `:::`

## Branches

- `quarto` — source branch, edit this one
- `gh-pages` — auto-generated build output, never edit
- `master` — the old Jekyll site, kept for reference
