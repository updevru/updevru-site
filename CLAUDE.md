# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Hugo static site for **updev.ru** — a personal website in Russian using the **Gokarna** theme (Git submodule at `themes/gokarna`).

## Build & Development

```bash
# Local dev server (Docker)
docker run -it --rm -p 1313:1313 -v ${PWD}:/src klakegg/hugo:ubuntu server

# Production build
hugo --minify
```

Output goes to `public/` (git-ignored). Deployed to GitHub Pages via `.github/workflows/gh-pages.yml` on push to `master`.

## Architecture

### Content Types

Pages use a `type` front matter field that controls rendering via `layouts/_default/list.html`:

- **`post`** — Articles, rendered as cards grouped by year. Use page bundles: `content/articles/<slug>/index.md` + images.
- **`page`** — Static pages (projects, resume). Uses theme's default page template.
- **`radar`** — Technology radar visualization at `/radar/`, rendered by `layouts/partials/radar.html`.

### Layout Overrides (over Gokarna theme)

- `layouts/_default/baseof.html` — Base HTML template with custom structure
- `layouts/_default/list.html` — Routes to partials based on content `type`
- `layouts/partials/list.html` — Article listing grouped by year
- `layouts/partials/list-posts.html` — Single article card
- `layouts/partials/radar.html` — Full tech radar (D3.js + Zalando radar-0.8.js) with inline data

### Tech Radar

Radar data is **hardcoded** in `layouts/partials/radar.html` inside the `entries` array. Each entry has: `quadrant` (0-3), `ring` (0=ADOPT, 1=TRIAL, 2=ASSESS, 3=HOLD), `label`, `active`, `moved` (0/1/-1). Quadrants: Languages & Frameworks (0), Infrastructure (1), Data Management (2), Techniques & Tools (3).

### Key Static Assets

- `static/CNAME` — Custom domain config (`updev.ru`)
- `static/css/base.css` — Custom CSS (radar layout, article cards, responsive)
- `static/tech-radar/js/` — D3.js v4 and Zalando radar library

## Git Submodule

The theme requires submodule initialization:
```bash
git submodule update --init --recursive
```

## Language & Locale

All content is in Russian. Config: `languageCode = "ru-ru"`, `defaultContentLanguage = "ru"`.
