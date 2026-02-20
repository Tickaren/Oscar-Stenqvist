# Portfolio Redesign Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Replace the outdated Bootstrap 4 personal site with a modern, dark-themed single-page portfolio using plain HTML/CSS/JS.

**Architecture:** Single `index.html` with six sections (Hero, About, Tech Stack, Projects, Experience, Contact). All styling via CSS custom properties in one stylesheet. Vanilla JS for typing animation, scroll-triggered fade-ins, and smooth nav. No frameworks, no build step.

**Tech Stack:** HTML5, modern CSS (Grid, custom properties, keyframes), vanilla JavaScript, Google Fonts (Inter, Space Grotesk, JetBrains Mono). Hosted on GitHub Pages.

**Design doc:** `docs/plans/2026-02-20-portfolio-redesign-design.md`

---

### Task 1: Clean up old dependencies

**Files:**
- Delete: `node_modules/` (entire directory)
- Delete: `package-lock.json`

**Step 1: Remove node_modules and package-lock.json**

```bash
rm -rf node_modules/ package-lock.json
```

**Step 2: Create js/ directory**

```bash
mkdir -p js
```

**Step 3: Commit**

```bash
git add -A
git commit -m "chore: remove old node_modules and package-lock.json"
```

---

### Task 2: Build the CSS foundation

**Files:**
- Rewrite: `css/styles.css`

**Step 1: Write the complete stylesheet**

Write `css/styles.css` with:

1. **CSS custom properties** on `:root`:
   - `--bg: #0a0a0a`
   - `--surface: #141414`
   - `--border: #1e1e1e`
   - `--accent: #00ff88`
   - `--accent2: #00b4d8`
   - `--text: #e0e0e0`
   - `--text-heading: #ffffff`
   - `--text-muted: #888888`
   - `--font-heading: 'Space Grotesk', sans-serif`
   - `--font-body: 'Inter', sans-serif`
   - `--font-mono: 'JetBrains Mono', monospace`
   - `--max-width: 1100px`

2. **Reset & base styles**: box-sizing border-box, zero margin/padding on body, background `var(--bg)`, color `var(--text)`, font-family `var(--font-body)`, smooth scrolling.

3. **Utility classes**: `.container` (max-width, centered, padding), `.section` (padding top/bottom ~6rem).

4. **Hero section**: 100vh, flex centered, animated gradient background (dark tones — `#0a0a0a` shifting to `#0d1117` and back), name in large font, typing cursor as a blinking `|` after the subtitle text.

5. **Navigation**: fixed top, translucent dark background with backdrop-filter blur, flex row of links, accent color on hover. Hidden on mobile, hamburger toggle.

6. **About section**: two-column grid (text + image), image with border-radius and subtle green glow border on hover.

7. **Tech stack section**: flex-wrap grid of tag pills — dark surface background, border, monospace font, accent color on hover.

8. **Project cards**: CSS Grid, 3 columns on desktop, 2 on tablet, 1 on mobile. Card: surface background, border, border-radius 8px, overflow hidden. Image on top, text below. Hover: translateY(-4px), box-shadow glow with accent color.

9. **Experience timeline**: vertical line on the left (accent color), cards offset to the right. Each card: surface background, border, date in muted text.

10. **Contact/footer**: centered, icon links styled large with hover accent glow.

11. **Scroll animations**: `.fade-in` class — starts with `opacity: 0; transform: translateY(20px)`, transitions to `opacity: 1; transform: translateY(0)` when `.visible` class is added.

12. **Responsive**: media queries for `max-width: 768px` — single columns, smaller headings, adjusted spacing, mobile nav.

**Step 2: Open in browser and verify**

Open `index.html` in browser. At this point it will be blank (HTML not written yet) but the CSS file should load without errors.

**Step 3: Commit**

```bash
git add css/styles.css
git commit -m "feat: add complete CSS foundation with dark theme and custom properties"
```

---

### Task 3: Build the HTML structure

**Files:**
- Rewrite: `index.html`

**Step 1: Write the complete HTML**

Write `index.html` with:

1. **Head**: charset, viewport meta, Google Fonts preconnect + stylesheet links (Inter, Space Grotesk, JetBrains Mono), link to `css/styles.css`, title "Oscar Stenqvist — Fullstack Developer", favicon (optional).

2. **Nav** (fixed): logo/name on left, section links on right (About, Tech, Projects, Experience, Contact). Hamburger button for mobile.

3. **Hero section** (`id="hero"`):
   - `<h1>Oscar Stenqvist</h1>`
   - `<p class="typing">` with `<span class="typed-text"></span><span class="cursor">|</span>`
   - Scroll-down indicator (chevron or arrow, animated bounce)

4. **About section** (`id="about"`):
   - Two-column grid
   - Left: heading "About Me", 2-3 sentences placeholder text. Example: "I'm a fullstack developer based in Sweden with a passion for building clean, performant applications. From mobile apps to backend systems, I enjoy working across the full stack. Outside of code, I compete in OCR races and spend time in the mountains."
   - Right: `<img src="img/oscar.jpg">` with class for styling

5. **Tech Stack section** (`id="tech"`):
   - Heading: "Tech Stack"
   - Category sub-headings: "Languages", "Frameworks & Libraries", "Tools & Platforms"
   - Under each: `<span class="tech-tag">JavaScript</span>` etc. Placeholder tags:
     - Languages: JavaScript, TypeScript, Python, Dart, Swift, C#, Java
     - Frameworks: React, Flutter, Node.js, Express, Firebase
     - Tools: Git, Docker, CI/CD, AWS, Figma

6. **Projects section** (`id="projects"`):
   - Heading: "Projects"
   - 3 placeholder project cards, each with:
     - Image placeholder (use existing images or a colored div)
     - Project name
     - Short description
     - Tech tags
     - Links (GitHub icon, external link icon)

7. **Experience section** (`id="experience"`):
   - Heading: "Experience"
   - Timeline with placeholder entries:
     - Entry 1: "Fullstack Developer — Company Name" / "2021 — Present" / short description
     - Entry 2: "App Developer — HiQ" / "2019 — 2021" / short description
     - Entry 3: "Education — Jonkoping University" / "2016 — 2019" / "BSc Software Development & Mobile Platforms"

8. **Contact section** (`id="contact"`):
   - Heading: "Get in Touch"
   - Paragraph: "Interested in working together? Feel free to reach out."
   - GitHub link (SVG icon or text)
   - LinkedIn link (SVG icon or text)
   - Email link

9. **Scripts**: `<script src="js/main.js"></script>` at end of body.

All content sections should have the `fade-in` class for scroll animation.

**Step 2: Open in browser and verify**

Open `index.html`. Should render all sections with dark theme, proper typography, layout. Some things won't animate yet (JS not written).

**Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add complete HTML structure with all portfolio sections"
```

---

### Task 4: Write the JavaScript

**Files:**
- Create: `js/main.js`

**Step 1: Write the complete JS file**

Write `js/main.js` with three features:

1. **Typing animation**:
   - Array of strings to type: `['Fullstack Developer', 'App Developer', 'Problem Solver']`
   - Type characters one at a time (100ms interval)
   - Pause at end of string (2000ms)
   - Delete characters (50ms interval)
   - Move to next string, loop forever
   - Target element: `.typed-text`

2. **Scroll-triggered fade-in**:
   - `IntersectionObserver` with `threshold: 0.1`
   - Observe all elements with class `fade-in`
   - When intersecting, add class `visible`
   - Once visible, `unobserve` the element (animate once)

3. **Mobile nav toggle**:
   - Click handler on hamburger button
   - Toggle a class on the nav links container to show/hide
   - Close menu when a nav link is clicked

4. **Active nav highlighting**:
   - `IntersectionObserver` on sections
   - When a section is in view, add `active` class to corresponding nav link

**Step 2: Open in browser and verify**

- Hero typing animation cycles through strings
- Sections fade in as you scroll down
- Nav links highlight the current section
- Mobile hamburger works on narrow viewport

**Step 3: Commit**

```bash
git add js/main.js
git commit -m "feat: add typing animation, scroll observer, and mobile nav JS"
```

---

### Task 5: Polish and responsive testing

**Files:**
- Modify: `css/styles.css` (tweaks)
- Modify: `index.html` (tweaks)

**Step 1: Test responsive breakpoints**

Open in browser, resize to mobile (375px), tablet (768px), desktop (1200px+). Fix any layout issues:
- Hero text sizing on mobile
- Project grid collapsing properly
- Nav hamburger menu working
- Images not overflowing

**Step 2: Add SVG icons for contact links**

Add inline SVGs for GitHub and LinkedIn icons in the contact section (no external icon library needed). Simple, recognizable icons.

**Step 3: Verify all animations**

- Scroll through entire page
- Confirm fade-ins trigger correctly
- Confirm typing animation loops
- Confirm hover effects on cards and links

**Step 4: Commit**

```bash
git add -A
git commit -m "feat: polish responsive layout, add SVG icons, finalize animations"
```

---

### Task 6: Final cleanup

**Files:**
- Possibly modify: `index.html` (remove old analytics)
- Keep: `.nojekyll`
- Keep: `README.md` (update if desired)
- Keep: `img/` (existing images)

**Step 1: Remove old Google Analytics tag**

The old `UA-40834948-2` tag should already be gone since we rewrote `index.html`. Verify it's not present.

**Step 2: Verify GitHub Pages compatibility**

- Confirm `.nojekyll` exists
- Confirm `index.html` is at root
- No build step needed

**Step 3: Final full-page review**

One last scroll through the complete site in browser at desktop and mobile widths.

**Step 4: Commit**

```bash
git add -A
git commit -m "chore: final cleanup and GitHub Pages verification"
```

---

## Summary

| Task | Description | Files |
|------|-------------|-------|
| 1 | Clean up old dependencies | Delete `node_modules/`, `package-lock.json` |
| 2 | CSS foundation | `css/styles.css` |
| 3 | HTML structure | `index.html` |
| 4 | JavaScript | `js/main.js` |
| 5 | Polish & responsive | `css/styles.css`, `index.html` |
| 6 | Final cleanup | Verification |
