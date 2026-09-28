# Personal Portfolio Website, PRD

## Overview

This is my personal portfolio website. The purpose of the site is to introduce myself, show my experiences and projects, and give visitors an easy way to learn more about me.

## Audience

The main audience includes:
- Recruiters and potential employers
- Professors and classmates
- Professional connections
- Anyone interested in learning more about me and my work

## Goals

The website should:
- Introduce who I am and my background
- Showcase my work experience
- Show my projects
- Highlight my involvement in clubs and organizations
- Provide access to my resume
- Make it easy to navigate between different parts of my portfolio

## Pages

### Home
Introduces me and provides an overview of the website.

### Resume
Displays my resume and professional background.

### Work Experience
Shows my previous and current work experience.

### Projects
Highlights projects I have worked on.

### About Me
Provides more information about me, my background, interests, and personality.

### Clubs
Shows clubs and organizations I am involved in.

## Design Direction

The website should feel creative, personal, playful, and polished.

The current website establishes the main visual direction. New pages and features should follow the existing design rather than creating a completely different style.

The design should maintain consistent:
- Colors
- Typography
- Navigation
- Spacing
- Layout
- Buttons and interactive elements

## Design System

### Colors
Defined as CSS custom properties (`:root`) on every page:

| Variable | Hex | Usage |
|---|---|---|
| `--teal` | `#AFEEEE` | Star accents, hover states, bullet icons |
| `--yellow` | `#FDEFB2` | Sidebar text, nav links, button accents, star tiles |
| `--overlay-yellow` | `#FFF2C4` | "Explore More" overlay background (index page only) |
| `--brown` | `#4A2A0D` | Primary text color, borders, sidebar/hero background |
| `--paper` | `#FBF9F4` | Page background (off-white/cream) |

Additional colors used directly (not tokenized, but consistent across pages):
- `#2AA9A9` (deep teal) — nav bar background, hero accent text/em, hover link color
- `rgba(45, 19, 0, 0.15)` — subtle borders/dividers on light backgrounds
- `rgba(74, 42, 13, 0.25)` — subtle list dividers

### Typography
Google Fonts loaded via `<link>`: **Instrument Serif** (italic/regular) and **Manrope** (weights 300–600).

Custom `@font-face` fonts (optional, in `/fonts`, fall back gracefully if files are missing):
- `Script` → `LuxuriousScript-Regular.ttf` (used for the cursive hero title)
- `Feature`, `Kensington`, `Obviously` → referenced but files not yet added; fall back to Instrument Serif / Manrope

Font variables (index page):
```css
--font-script: 'Script', 'Instrument Serif', cursive;   /* hero title */
--font-display: 'Kensington', 'Instrument Serif', serif;
--font-heading: 'Feature', 'Instrument Serif', serif;
--font-body: 'Obviously', 'Manrope', sans-serif;
```

Practical usage across pages:
- Body text: `'Manrope', sans-serif`, weight `300`, `line-height: 1.8`, `letter-spacing: 0.01em`
- Headings (`h1`, `h2`, `.sidebar h3`, `.explore-overlay h2/h3`): `'Cormorant Garamond', serif`, weight `500`
- `h1`: `3.4em`, `line-height: 1.1`; `em` inside `h1` is colored `#2AA9A9`
- `h2`: `1.9em`, top border-bottom divider (`rgba(45,19,0,0.15)`)
- Hero title (index only): `var(--font-script)`, two stacked lines (`.hero-line-1` brown, `.hero-line-2` teal `#2AA9A9`), sizes via `clamp()`
- Eyebrow labels: `0.75em`, uppercase, `letter-spacing: 0.22em`, `opacity: 0.65`
- Nav links: uppercase, `0.78em`, `letter-spacing: 0.14em`

### Layout & Spacing
- Fixed left `.sidebar` (260px wide, brown background, yellow text) present on the home page; other pages use a simpler top-nav-only layout with `main { max-width: 980px; margin: 0 auto; }`
- Sticky `nav` bar, teal (`#2AA9A9`) background, full-bleed via negative margins (`margin: 0 -32px ...`), centered uppercase links with underline-on-hover (`::after` width transition)
- Page body padding: `0 32px 100px` desktop, tightened to `0 20px 70px` on mobile
- Consistent divider style: `1px solid rgba(45, 19, 0, 0.15)` under nav, headings, footer

### Buttons & Interactive Elements
- Nav links/buttons: transparent background, underline grows from 0 to 100% width on hover/focus
- `.explore-button` / pill tags: `border: 1px solid`, transparent background, fills solid on hover (brown↔yellow or brown↔paper swap)
- `.hero-star`: clipped star-shaped links/buttons in yellow/teal/brown, scale + slight rotate on hover
- List items (`ul.list`, `.explore-list`): star bullet (`\2605`) in teal with brown outline, shifts color and slides right on hover
- Rounded pill tags (`border-radius: 999px`) for skill/tag chips
- Custom SVG star-shaped cursor (`#cursor-dot`) replaces the native cursor on hover-capable devices, spins continuously, and changes fill color depending on what it's hovering over

### Motion
- Smooth scroll (`scroll-behavior: smooth`)
- `.reveal` sections fade/slide in on scroll (`opacity`/`translateY` transition, `.in-view` class toggled via JS)
- Marquee-style scrolling tag row (`@keyframes marquee`, pauses on hover)

## Responsive Design

The website should work on both desktop and mobile devices.

Content should remain readable and navigation should remain usable as the screen size changes.

## Future Improvements

The website can continue to evolve as I gain more experience and complete more projects. New content and pages should be added without losing the existing visual identity of the site.