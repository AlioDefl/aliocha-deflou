# CLAUDE.md - AI Assistant Guide

This document provides comprehensive guidance for AI assistants working with this codebase.

## Project Overview

**Aliocha Deflou's Personal Portfolio Website** - A static HTML-based portfolio and CV website for a computer science student (BUT Informatique at IUT de Lille).

- **Type**: Static website (no backend/database)
- **Language**: French content, English technical terms
- **Hosting**: GitHub Pages at `aliodefl.github.io/aliocha-deflou/`
- **Deployment**: Automated via GitHub Actions on push to `main`

## Repository Structure

```
aliocha-deflou/
├── .github/
│   └── workflows/
│       └── static.yml          # GitHub Pages deployment workflow
├── index.html                  # Main portfolio/home page
├── formations.html             # Education/training page
├── projets.html                # Projects showcase page
├── CV_Aliocha_DEFLOU.pdf       # Downloadable CV document
├── google8f8cc0aa71974e07.html # Google site verification
├── favicon.png                 # Site favicon
├── og-image.png                # Open Graph preview image
├── robots.txt                  # Search engine crawling rules
└── sitemap.xml                 # XML sitemap for SEO
```

## Technical Architecture

### No Build System
This is a **pure static site** with no build tools, bundlers, or package managers. All code is embedded inline.

### CSS Approach
- **Inline embedded CSS** in `<style>` tags within each HTML file
- **CSS Variables** for theming:
  ```css
  --bg: #fafafa       /* Background */
  --text: #1a1a1a     /* Primary text */
  --text-light: #666  /* Secondary text */
  --text-muted: #999  /* Muted text */
  --border: #e5e5e5   /* Border color */
  --accent: #000      /* Accent color */
  ```
- **Typography**: IBM Plex Sans (main), IBM Plex Mono (accents) via Google Fonts
- **Responsive breakpoints**: 768px (tablet), 500px (mobile)

### JavaScript Approach
- **Inline embedded JavaScript** in `<script>` tags
- **Vanilla JavaScript** only (no frameworks)
- Key features: Modal system, custom cursor, scroll animations, parallax effects

### HTML Structure
- Semantic HTML5 with proper accessibility
- ARIA labels for interactive elements
- JSON-LD structured data for SEO
- Open Graph meta tags for social sharing

## Development Workflow

### Making Changes
1. Edit HTML files directly (no compilation needed)
2. Test locally by opening HTML files in a browser
3. Commit and push to `main` branch
4. GitHub Actions automatically deploys to GitHub Pages

### Deployment
- **Trigger**: Push to `main` branch or manual workflow dispatch
- **Process**: Entire repository root is uploaded and deployed
- **URL**: https://aliodefl.github.io/aliocha-deflou/

## Code Conventions

### Naming
- CSS classes use lowercase with hyphens: `.nav-links`, `.skill-item`
- JavaScript uses camelCase: `showModal()`, `projectsData`
- Content in French, code/comments in English

### File Organization
- Each page is self-contained with its own CSS and JS
- Shared styles are duplicated (intentional for simplicity)
- No external CSS/JS files to minimize HTTP requests

### Accessibility Requirements
- All interactive elements need ARIA labels
- Keyboard navigation support (Tab, Enter, Escape)
- Semantic HTML elements (header, main, section, article, footer)
- Skip-to-main-content link included
- Proper heading hierarchy (h1 > h2 > h3)

### SEO Requirements
When modifying pages, maintain:
- Title and meta description tags
- Open Graph tags (og:title, og:description, og:image)
- Canonical URL
- JSON-LD structured data
- Update sitemap.xml `lastmod` dates when content changes

## Page-Specific Details

### index.html (Homepage)
Main sections: Hero, Formations overview, Experiences, Projects preview, Skills, Contact, Legal modal

### formations.html (Education)
Lists educational background chronologically with certifications

### projets.html (Projects)
Project showcase with modal popups for details. Projects data stored as JavaScript object.

## Common Tasks

### Adding a New Project
1. Edit `projets.html`
2. Add project card in the projects grid section
3. Add project data to the `projectsData` JavaScript object
4. Update sitemap.xml `lastmod` date

### Updating Contact Information
1. Update in `index.html` contact section
2. Update JSON-LD structured data
3. Update any mailto links

### Modifying Styles
1. Find the `<style>` block in the relevant HTML file
2. CSS variables are at the top of the style block
3. Media queries for responsive styles are at the end

## Important Files Reference

| File | Purpose | Key Sections |
|------|---------|--------------|
| `index.html` | Main landing page | Hero, experiences, skills, contact |
| `formations.html` | Education details | School history, certifications |
| `projets.html` | Project portfolio | Project cards, modal popups |
| `static.yml` | Deployment config | GitHub Actions workflow |
| `sitemap.xml` | SEO sitemap | Update lastmod on content changes |

## Testing Checklist

Before pushing changes:
- [ ] Open modified pages in browser
- [ ] Test on mobile viewport (responsive)
- [ ] Verify all links work
- [ ] Check modal open/close functionality
- [ ] Test keyboard navigation
- [ ] Validate HTML (no console errors)

## Constraints & Guidelines

1. **Keep it simple**: No build tools, frameworks, or external dependencies
2. **Performance first**: Inline CSS/JS to minimize requests
3. **Accessibility**: Every change must maintain WCAG compliance
4. **SEO**: Update meta tags and sitemap when content changes
5. **Bilingual**: Content in French, code in English
6. **Self-contained**: Each HTML file should work independently
