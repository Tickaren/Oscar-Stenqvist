# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal portfolio website for Oscar Stenqvist, hosted on GitHub Pages. Static single-page site with no build step — just open `index.html` in a browser.

## Current Tech Stack

- HTML5, CSS, vanilla JavaScript (inline in `index.html`)
- Bootstrap 4.3.1, jQuery 3.3.1, Popper.js (all via CDN)
- AOS (Animate On Scroll) v2.3.4 (from `node_modules/`)
- Google Analytics (UA-40834948-2)
- Content is in Swedish

## Active Redesign Plan

A full redesign is documented in `docs/plans/`:
- `2026-02-20-portfolio-redesign.md` — 6-task implementation plan
- `2026-02-20-portfolio-redesign-design.md` — visual design spec

The redesign replaces Bootstrap/jQuery/AOS with plain HTML/CSS/JS, adds a dark theme (terminal green `#00ff88` accent), uses Google Fonts (Inter, Space Grotesk, JetBrains Mono), and rewrites all content in English. Target file structure: `index.html`, `css/styles.css`, `js/main.js`.

## Development

No build commands, no tests, no linter. To preview changes, open `index.html` directly in a browser.

**GitHub Pages requirements:**
- `.nojekyll` must exist at root (disables Jekyll processing)
- `index.html` must be at root

## File Structure

```
index.html          — entire site (single page, ~300 lines)
css/styles.css      — custom styles (Bootstrap does the heavy lifting currently)
img/                — all images (oscar.jpg, project screenshots, social icons)
docs/plans/         — redesign planning documents
node_modules/       — AOS library only (to be removed in redesign)
```

## Key Architectural Notes

- Everything lives in one HTML file — nav, all content sections, inline JS at the bottom
- AOS handles all scroll animations via `data-aos` attributes
- Navigation uses Bootstrap's scrollspy (`data-spy="scroll"`) with manual scroll offset JS
- The site has no routing — section IDs (`#hero`, `#section1`–`#section4`) handle in-page navigation
