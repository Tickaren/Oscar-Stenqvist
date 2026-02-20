# Portfolio Redesign — Design Document

## Goal

Replace the existing outdated personal website with a modern, dark-themed professional portfolio showcasing Oscar Stenqvist as a fullstack developer.

## Decisions

- **Type:** Professional portfolio
- **Content:** Fresh start — all new English content
- **Style:** Dark & techy (terminal-inspired accents, dark backgrounds)
- **Language:** English
- **Tech stack:** Plain HTML / CSS / JS — no frameworks, no build step
- **Structure:** Single-page scroll
- **Hosting:** GitHub Pages (existing setup)

## Visual Foundation

### Color Palette

| Role             | Value     |
|------------------|-----------|
| Background       | `#0a0a0a` |
| Surface/cards    | `#141414` |
| Card border      | `#1e1e1e` |
| Primary accent   | `#00ff88` (terminal green) |
| Secondary accent | `#00b4d8` (cyan) |
| Heading text     | `#ffffff` |
| Body text        | `#e0e0e0` |
| Muted text       | `#888888` |

### Typography

- **Headings:** Space Grotesk (Google Fonts)
- **Body:** Inter (Google Fonts)
- **Code/accents:** JetBrains Mono (Google Fonts)

### Animations

- Fade-in-up on scroll via CSS `@keyframes` + `IntersectionObserver`
- Typing cursor animation on hero subtitle
- Subtle hover transitions on cards and links (scale, glow)

### Layout

- Max content width: ~1100px, centered
- CSS Grid for project cards
- Responsive: single column mobile, multi-column desktop
- Generous section spacing

## Page Sections

### 1. Hero (100vh)

- Dark background with subtle animated gradient
- Name: "Oscar Stenqvist" (large heading)
- Typing animation subtitle: `> Fullstack Developer`
- Nav links: About / Projects / Experience / Contact
- Scroll-down indicator

### 2. About

- 2-3 sentence developer intro
- Optional photo (oscar.jpg exists)
- Brief personality note (OCR/outdoor interests)

### 3. Tech Stack

- Grid of tech tags/icons organized by category
- Categories: Languages, Frameworks, Tools
- Visual — icons with labels, not paragraphs

### 4. Projects

- 2-3 column card grid (desktop)
- Each card: name, description, tech tags, image, links (GitHub/live)
- Hover: subtle glow/lift effect
- Placeholder cards for Oscar to fill in

### 5. Experience

- Vertical timeline or stacked cards
- Fields: company, role, dates, brief description
- Most recent first

### 6. Contact / Footer

- GitHub and LinkedIn icons (styled, large)
- Email link
- Clean and simple, no form

## File Structure

```
index.html          — single page, all sections
css/styles.css      — styles with CSS custom properties
js/main.js          — typing animation, scroll observer, nav
img/                — images (keep existing, add new as needed)
.nojekyll           — keep for GitHub Pages
```

## Cleanup

- Remove: Bootstrap 4, jQuery, Popper.js, AOS
- Remove: `node_modules/` directory, `package-lock.json`
- Remove or replace: old Google Analytics tag (UA-*)
- Replace: all Swedish content with English placeholders
