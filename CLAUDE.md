# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A single-file personal portfolio website for 성철스님 (kseil14). Everything — HTML, CSS, and JS — lives in `index.html`. There is no build step, no package manager, and no dependencies beyond Google Fonts loaded via `<link>`.

## Running the site

Open `index.html` directly in a browser. No server required. For quick iteration with live reload:

```bash
# Python (built-in)
python3 -m http.server 8080

# Node (if npx available)
npx serve .
```

## Design system

All colors are CSS custom properties defined in `:root`:

| Variable | Role |
|---|---|
| `--bg` | Page background (`#09090b`) |
| `--surface` | Slightly lighter surface |
| `--panel` | Card backgrounds |
| `--border` | Default border color |
| `--text` | Primary text (`#fafafa`) |
| `--muted` | Secondary/dim text |
| `--subtle` | Hover border states |
| `--accent-1` | Orange (`#f97316`) |
| `--accent-2` | Purple (`#a855f7`) |
| `--accent-3` | Cyan (`#06b6d4`) |
| `--glow` | Purple box-shadow glow |

Fonts: **Space Grotesk** for body text, **JetBrains Mono** for labels, tags, and monospace elements.

## Bento grid layout

The About section uses a 12-column CSS grid with fixed row height (`grid-auto-rows: 80px`). Column and row spans are set via utility classes:

- Columns: `.col-4`, `.col-5`, `.col-6`, `.col-7`, `.col-8`, `.col-12`
- Rows: `.row-2`, `.row-3`, `.row-4`, `.row-5`

When adding or resizing bento cells, ensure column spans in a row sum to 12 (or wrap intentionally). At the 900 px breakpoint all cells collapse to `span 12`.

## Page sections

| Section | Anchor | Notes |
|---|---|---|
| Hero | (top) | Gradient card with animated background layers |
| About | `#about` | Bento grid with stat cards, skills, philosophy |
| Projects | `#projects` | Auto-fill card grid; update project cards here |
| Contact | `#contact` | Email + social links |
| Footer | — | Copyright + nav links |

## JavaScript

Two lightweight behaviors, both inline at the bottom of `<body>`:

1. **Navbar scroll effect** — adds `.scrolled` class (shows border) after 20 px of scroll.
2. **Fade-in on scroll** — `IntersectionObserver` at 0.1 threshold animates `.bento-cell`, `.project-card`, and `.contact-card` from `opacity: 0 / translateY(20px)` to visible.

No frameworks, no modules, no transpilation.

## Content language

Body copy is in Korean. Keep new user-facing text in Korean unless the existing section uses English (e.g., section headings like "The full picture", skill tag names, and project type labels are intentionally in English).

## Updating projects

Project cards are `<a class="project-card">` elements inside `#projects .project-grid`. Each card has:
- `.project-thumb` — gradient background set inline via `style`
- `.project-type` — category label (English)
- `.project-name` — title
- `.project-desc` — description (Korean or English)
- `.project-tech` — `<span>` tags for the tech stack

## Social / contact links

- Email: `kseil14@naver.com` (in `.contact-email`)
- GitHub: `https://github.com/kseil14`
- LinkedIn: set in `.social-links`
- Twitter/X: `https://x.com/kseil1414`
