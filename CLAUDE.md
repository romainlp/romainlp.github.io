# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static landing page for the **Amp Control** iOS app, hosted on GitHub Pages (`romainlp.github.io`). It is a single self-contained HTML file with no build step, no package manager, and no external dependencies.

## Development

No build tools are required. To preview locally, open `index.html` directly in a browser or use any static file server:

```sh
python3 -m http.server 8080
```

Deployment happens automatically via GitHub Pages on push to `main`.

## Architecture

Everything lives in `index.html`:

- **CSS**: Inline `<style>` block using CSS custom properties for dark/light theming. The dark theme is default; light mode is applied by toggling `.light` on `<body>`.
- **HTML**: Single-page layout with sections: `nav`, `#hero`, `#features`, `footer`.
- **JS**: Inline `<script>` at the bottom. Handles theme toggling (persisted via `localStorage`) and scroll-reveal animations via `IntersectionObserver`.

Assets:
- `screenshot.png` — app screenshot used in the hero section.

## Conventions

- All styles are in the `<style>` block; do not introduce external CSS files.
- All scripts are in the `<script>` block; do not introduce external JS files or bundlers.
- Responsive breakpoint is at `600px`.
