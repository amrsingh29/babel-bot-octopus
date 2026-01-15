# Personal Portfolio Website - Project Guide

## Project Overview

This is a professional personal portfolio website for **Amar Singh**, built with Hugo static site generator, Tailwind CSS, and deployed on GitHub Pages. The site showcases executive-level thinking frameworks, applied case studies, and professional credibility targeting CIO/CTO/Founder audiences.

## Project Context

**Owner**: Amar Singh  
**Role**: Principal Solution Consultant at BMC  
**Specialization**: BMC Helix AIOps, AI agent solutions, ITSM  
**Target Audience**: CIOs, CTOs, Founders evaluating for collaboration or recruitment  
**Design Inspiration**: Modern SaaS marketing aesthetic (Observe.AI style)

## Technology Stack

- **Static Site Generator**: Hugo (v0.120+)
- **CSS Framework**: Tailwind CSS v3+
- **Hosting**: GitHub Pages
- **Version Control**: GitHub
- **CI/CD**: GitHub Actions
- **Content Format**: Markdown with YAML frontmatter

## Project Goals

1. **Executive-focused content hierarchy**: Home → Thinking → Work → Case Studies → About
2. **Modern, professional design**: Clean layouts, strategic whitespace, contemporary typography
3. **Performance**: Lighthouse score ≥ 90, fast page loads, optimized images
4. **Maintainability**: Easy content updates via Markdown files
5. **Responsive design**: Mobile-first, accessible, cross-browser compatible

## Site Structure

```
/
├── Home (/)
│   ├── Hero section with positioning statement
│   ├── Value proposition (3-5 key pillars)
│   ├── Social proof (company logos)
│   └── Call-to-action
│
├── Thinking (/thinking)
│   ├── Introduction to thinking framework
│   └── 4 Core Pillars:
│       ├── Autonomy
│       ├── Governance
│       ├── Evaluation
│       └── Human-in-the-loop
│
├── Work (/work)
│   ├── Case study cards (3-5 curated projects)
│   ├── Filters by category (ITSM, HR, Observability)
│   └── Key takeaways section
│
├── Case Studies (/work/[case-name])
│   ├── Challenge
│   ├── Decision Points (with diagrams/tables)
│   ├── Approach
│   ├── Outcome
│   └── Key Learnings
│
└── About (/about)
    ├── Executive bio
    ├── Experience highlights
    └── Professional credibility

```

## Design System

### Typography
- **Display Font**: DM Sans, Plus Jakarta Sans, Manrope, or Epilogue (avoid Inter, Roboto, Arial)
- **Body Font**: Crimson Pro, Source Serif, or refined sans-serif
- **Scale**:
  - Hero headline: 56-72px (desktop), 36-48px (mobile)
  - Section titles: 32-40px
  - Body text: 16-18px
  - Line height: 1.6 (body), 1.2 (headlines)

### Colors
- **Primary**: Professional navy, slate blue, or muted teal (avoid generic purple)
- **Secondary**: Complementary accent for CTAs
- **Neutral**: Gray scale (50-900)
- **Background**: Off-white or light warm gray
- **Text**: Near-black for primary, gray-700 for secondary

### Spacing
- Base unit: 4px or 8px
- Section padding: 80-120px vertical (desktop), 48-64px (mobile)
- Component spacing: Consistent Tailwind scale

### Components
1. **Navigation**: Sticky/fixed, logo + menu + CTA, mobile hamburger
2. **Hero**: Full viewport or 70vh, large headline + subheadline + CTAs
3. **Cards**: Subtle shadow, hover effects, 8-12px border radius
4. **Buttons**: Primary (filled), Secondary (outlined), hover transitions
5. **Logo Strip**: Grayscale logos, responsive grid
6. **Callouts**: Background variation, border-left accent

## Content Guidelines

### Markdown Front Matter Structure
```yaml
---
title: "Page or Case Study Title"
date: 2025-01-15
draft: false
category: "ITSM" # or "HR", "Observability"
summary: "Brief summary for card display"
image: "/images/case-hero.jpg" # optional
tags: ["AI Agents", "ITSM", "Automation"] # optional
---
```

### Writing Style
- **Executive-focused**: Emphasize judgment, decision-making, operational thinking
- **Professional tone**: Clear, concise, credible
- **Evidence-based**: Include metrics, outcomes, business impact
- **Visual hierarchy**: Use headings, bullets, tables where appropriate

### Required Content Files
All content should be provided in Markdown format:
- `content/_index.md` (home page)
- `content/thinking.md`
- `content/work/_index.md`
- `content/work/case-*.md` (individual case studies)
- `content/about.md`

## Development Workflow

### Initial Setup
1. Initialize Hugo project with extended version
2. Configure Tailwind CSS with custom theme
3. Set up base layout templates (baseof.html, header, footer)
4. Create component library (cards, buttons, navigation)
5. Integrate existing Markdown content

### Component Development
1. Build reusable Hugo partials for common elements
2. Implement responsive layouts using Tailwind
3. Add hover states and micro-interactions
4. Ensure accessibility (ARIA labels, keyboard nav, contrast)

### Content Integration
1. Set up content directory structure
2. Configure Hugo to process front matter
3. Create list and single page templates
4. Implement taxonomy for case categories

### Deployment Setup
1. Configure GitHub Actions workflow
2. Set up build process (Hugo + Tailwind)
3. Configure GitHub Pages deployment
4. Test deployment pipeline

### Testing & Optimization
1. Responsive testing (mobile, tablet, desktop)
2. Performance optimization (Lighthouse audit)
3. Accessibility testing (WCAG 2.1 AA)
4. Cross-browser testing
5. SEO metadata verification

## File Organization

```
portfolio-website/
├── config.toml (or hugo.toml)
├── package.json (Node dependencies)
├── tailwind.config.js
├── postcss.config.js
│
├── content/
│   ├── _index.md (home)
│   ├── thinking.md
│   ├── work/
│   │   ├── _index.md
│   │   ├── case-helixgpt.md
│   │   ├── case-hr-automation.md
│   │   └── case-pos.md
│   └── about.md
│
├── layouts/
│   ├── _default/
│   │   ├── baseof.html
│   │   ├── single.html
│   │   └── list.html
│   ├── partials/
│   │   ├── head.html
│   │   ├── header.html
│   │   ├── footer.html
│   │   ├── hero.html
│   │   ├── card.html
│   │   └── navigation.html
│   ├── index.html (home page)
│   └── shortcodes/
│       ├── callout.html
│       └── diagram.html
│
├── static/
│   ├── images/
│   ├── diagrams/
│   └── logos/
│
├── assets/
│   └── css/
│       └── main.css (Tailwind source)
│
├── .github/
│   └── workflows/
│       └── deploy.yml
│
└── public/ (generated, not committed)
```

## GitHub Actions Workflow

Deploy automatically on push to main branch:

```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Setup Hugo
        uses: peaceiris/actions-hugo@v2
        with:
          hugo-version: 'latest'
          extended: true
      
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      
      - name: Install dependencies
        run: npm ci
      
      - name: Build with Hugo
        run: hugo --minify
      
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

## Key Development Principles

### 1. Content-First Approach
- Content structure drives template design
- Easy Markdown authoring workflow
- Front matter for metadata management
- Reusable shortcodes for special elements

### 2. Progressive Enhancement
- Base HTML/CSS works without JavaScript
- Add interactions for enhanced experience
- Graceful degradation for older browsers

### 3. Performance Optimization
- Image optimization (WebP with JPEG fallback)
- Lazy loading for below-fold images
- Minified CSS/JS in production
- Critical CSS inlining for above-fold content

### 4. Accessibility First
- Semantic HTML structure
- ARIA labels where needed
- Keyboard navigation support
- Color contrast compliance (WCAG AA)
- Focus indicators visible
- Alt text for all images

### 5. Mobile-First Design
- Design for mobile, enhance for desktop
- Touch-friendly interactive elements (min 44x44px)
- Readable text sizes (min 16px body)
- Test on multiple devices

### 6. Maintainability
- Clear code organization
- Reusable Hugo partials
- Documented Tailwind classes
- Version control best practices
- Descriptive commit messages

## Common Tasks

### Adding New Case Study
1. Create new file: `content/work/case-{name}.md`
2. Add front matter with title, category, summary, image
3. Write content using Markdown
4. Add diagrams to `static/diagrams/`
5. Commit and push to trigger deployment

### Updating Thinking Framework
1. Edit `content/thinking.md`
2. Update pillar descriptions
3. Add/update diagrams if needed
4. Commit and push

### Changing Design System
1. Edit `tailwind.config.js` for colors, fonts, spacing
2. Update CSS in `assets/css/main.css`
3. Rebuild: `npm run build`
4. Test locally: `hugo server`
5. Commit changes

### Adding New Component
1. Create partial in `layouts/partials/{component}.html`
2. Style with Tailwind classes
3. Document usage in this file
4. Test in multiple contexts
5. Commit with clear description

## Testing Checklist

Before deployment, verify:
- [ ] All pages render correctly
- [ ] Navigation works on all pages
- [ ] Mobile responsive (test on 320px, 768px, 1024px, 1280px)
- [ ] Images load properly with alt text
- [ ] Links work (internal and external)
- [ ] Forms submit correctly (if any)
- [ ] Lighthouse score ≥ 90 (Performance, Accessibility, SEO)
- [ ] Browser compatibility (Chrome, Firefox, Safari, Edge)
- [ ] Keyboard navigation works
- [ ] Color contrast meets WCAG AA
- [ ] Meta tags present (title, description, OG tags)

## Troubleshooting

### Hugo Build Fails
- Check Hugo version (requires extended version for Sass/SCSS)
- Verify content front matter syntax (YAML formatting)
- Look for template errors in layouts
- Check for missing partials or resources

### Tailwind Not Working
- Ensure postcss.config.js is configured
- Verify tailwind.config.js content paths
- Check that npm dependencies are installed
- Rebuild CSS: `npm run build`

### GitHub Pages Not Deploying
- Check Actions tab for build errors
- Verify GitHub Pages is enabled in repo settings
- Ensure deploy.yml has correct permissions
- Check that public/ directory is generated correctly

### Images Not Loading
- Verify image paths (relative to static/)
- Check file extensions (case-sensitive)
- Ensure images are in static/ directory
- Check browser console for 404 errors

## Performance Targets

- **Lighthouse Performance**: ≥ 90
- **First Contentful Paint**: < 1.8s
- **Largest Contentful Paint**: < 2.5s
- **Total Blocking Time**: < 200ms
- **Cumulative Layout Shift**: < 0.1
- **Time to Interactive**: < 3.5s

## SEO Requirements

Each page must include:
- Unique, descriptive `<title>` (50-60 chars)
- Meta description (150-160 chars)
- Open Graph tags (og:title, og:description, og:image)
- Twitter Card tags
- Canonical URL
- Structured data (JSON-LD for Person/Organization)

## Accessibility Requirements

Must meet WCAG 2.1 Level AA:
- Color contrast ratio ≥ 4.5:1 for normal text
- Color contrast ratio ≥ 3:1 for large text and UI components
- Keyboard navigation for all interactive elements
- Focus indicators visible and clear
- ARIA labels for icon buttons
- Alt text for informative images
- Proper heading hierarchy (no skipped levels)
- Form labels associated with inputs

## Browser Support

**Target browsers:**
- Chrome/Edge (last 2 versions)
- Firefox (last 2 versions)
- Safari (last 2 versions)
- Mobile Safari (iOS 14+)
- Chrome Mobile (Android 10+)

## Future Enhancements

**Phase 2 (post-launch):**
- [ ] Blog/Notes section for insights
- [ ] Case study filtering by category
- [ ] Light/Dark mode toggle
- [ ] Interactive diagrams with JavaScript
- [ ] Contact form with serverless function

**Phase 3 (advanced):**
- [ ] Search functionality (Algolia or Pagefind)
- [ ] Analytics integration (privacy-focused)
- [ ] RSS feed for blog content
- [ ] PWA features (offline support)
- [ ] Downloadable resume/CV

## Resources

**Hugo Documentation**: https://gohugo.io/documentation/  
**Tailwind CSS Docs**: https://tailwindcss.com/docs  
**GitHub Pages Guide**: https://docs.github.com/en/pages  
**Accessibility Guidelines**: https://www.w3.org/WAI/WCAG21/quickref/  
**Lighthouse Documentation**: https://developer.chrome.com/docs/lighthouse/

## Notes for Claude Code

### When Building
1. Start by reading the full PRD (`PRD_Updated.md`)
2. Set up Hugo + Tailwind project structure first
3. Configure Tailwind with custom design system
4. Build component library before page templates
5. Integrate Markdown content last
6. Test thoroughly before deployment setup

### When Maintaining
1. Check existing partials before creating new ones
2. Follow established Tailwind utility patterns
3. Update this CLAUDE.md when adding features
4. Run local build before pushing changes
5. Monitor Lighthouse scores after changes

### Code Quality Standards
- Use semantic HTML5 elements
- Follow BEM-like naming for custom classes
- Comment complex Tailwind combinations
- Extract repeated patterns into partials
- Keep templates DRY (Don't Repeat Yourself)
- Use Hugo's built-in functions when possible

### Content Guidelines for User
- All content should be in Markdown
- Use front matter for metadata
- Keep paragraphs concise (3-4 sentences)
- Use bullet points for scanability
- Include metrics and outcomes
- Add diagrams where helpful
- Maintain professional, executive tone

---

**Last Updated**: 2026-01-15  
**Project Status**: Initial Development  
**Version**: 1.0.0
