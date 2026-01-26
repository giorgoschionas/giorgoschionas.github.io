# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based academic portfolio website (Academic Pages template). Content is written in Markdown with YAML front matter, rendered via Liquid templates, and styled with SCSS.

## Build & Development Commands

```bash
# Local development (requires Ruby/Bundler)
bundle install
bundle exec jekyll serve -l -H localhost

# Docker development
docker compose up
# Server at localhost:4000

# JavaScript build (minification)
npm install
npm run build:js
```

## Architecture

### Collections (in `_config.yml`)
Content is organized into Jekyll collections, each with its own directory:
- `_publications/` - Research papers (categorized: books, manuscripts, conferences)
- `_talks/` - Conference talks
- `_teaching/` - Teaching materials
- `_portfolio/` - Project portfolio
- `_posts/` - Blog posts
- `_pages/` - Static pages (about, cv, publications listing, etc.)

### Publication Front Matter
Publications use this YAML structure:
```yaml
---
title: "Paper Title"
collection: publications
category: conferences  # or: books, manuscripts
permalink: /publication/YYYY-slug
paperurl: 'https://...'
venue: 'Conference Name (ACRONYM YYYY)'
authors: 'Author1, Author2, Author3'
citation: 'Author1, Author2, Author3.'
---
```

### Key Files
- `_config.yml` - Main Jekyll config (site settings, collections, defaults)
- `_data/navigation.yml` - Site navigation menu
- `_data/cv.json` - CV data (generated from markdown via `scripts/cv_markdown_to_json.py`)
- `_includes/archive-single.html` - Template for rendering collection items
- `_sass/layout/_archive.scss` - Styling for publication/archive listings

### Styling
- SCSS in `_sass/` compiled via Jekyll
- Themes available: default, air, sunrise, mint, dirt, contrast (set `site_theme` in `_config.yml`)
- Custom styles for publications/archives in `_sass/layout/_archive.scss`

### Content Generation
The `markdown_generator/` directory contains Jupyter notebooks and Python scripts for bulk content creation:
- `publications.ipynb` / `publications.py` - TSV to publication markdown
- `talks.ipynb` / `talks.py` - TSV to talk markdown
- `PubsFromBib.ipynb` - BibTeX import

## Publication Categories

Publications are grouped by category (defined in `_config.yml`):
- `books` - Books
- `manuscripts` - Journal Articles
- `conferences` - Conference Papers

The category determines which heading the publication appears under on the publications page.
