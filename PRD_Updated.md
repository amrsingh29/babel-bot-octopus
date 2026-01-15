Product Requirements Document (PRD) — Personal Portfolio Website
Owner: Amar Singh
Date: 2026-01-15
Platform: Hugo static site generator + Tailwind CSS
Hosting: GitHub Pages
Reference Design: Modern marketing site aesthetic (Observe.AI style)

---

## 1. Purpose / Objective

Build a professional personal portfolio website that combines executive-level narrative with modern, polished design to showcase:
- Executive-level narrative (Home page, Thinking framework)
- Applied case studies (Work page)
- Drill-down deep-dives for projects
- Professional biography and credibility

The target audience is CIO / CTO / Founder, so the content must emphasize judgment, decision-making, and operational thinking, not just technical skills.

The website must be fast, responsive, easily maintainable, and support content creation in Markdown via Hugo. Tailwind CSS should provide a modern, clean design inspired by contemporary SaaS marketing sites, and the site should be deployable on GitHub Pages.

---

## 2. Goals

- **Audience-focused design**: First impression communicates executive-level thinking and credibility with modern, professional aesthetics
- **Content-first hierarchy**: Content aligns with senior leader POV:
  Home → Thinking → Work → Drill-down case studies → About / Credibility
- **Modern visual design**: Clean, spacious layouts with strategic use of imagery, typography hierarchy, and whitespace
- **Responsive & performant**: Mobile-friendly, fast-loading, and SEO-friendly
- **Markdown-based workflow**: Easy updates via Markdown files for content creators
- **Reusability**: Components for work cases, thinking pillars, diagrams, and callouts
- **Automated deployment**: CI/CD workflow to push changes to GitHub Pages

---

## 3. Target Audience

**Primary**: CIOs, CTOs, Founders evaluating portfolio for collaboration, consulting, or recruitment
**Secondary**: Technical peers, recruiters, or domain experts exploring work and frameworks

---

## 4. Site Structure & Pages

### 4.1 Home Page (Landing Page)

**Layout inspired by modern SaaS marketing sites:**

**Hero Section:**
- Large, bold headline establishing professional positioning
- Subheadline explaining value proposition
- 2 CTA buttons: "How I Think" (primary) and "View Work" (secondary)
- Hero image or visual element (professional photo or abstract illustration)
- Ample whitespace and generous padding

**Value Proposition Section:**
- 3-5 key pillars displayed as cards or columns
- Each with icon/visual, title, and brief description
- Clean grid layout with hover effects

**Social Proof / Credibility Section:**
- Logo strip showing companies/organizations worked with
- Simple, grayscale logos on clean background
- Optional: Brief testimonial or quote

**Call-to-Action Section:**
- Secondary CTA encouraging visitors to explore thinking or work
- Clean, modern button styling

**Design Requirements:**
- Modern navigation bar (sticky/fixed)
- Large typography for headlines (64-72px range)
- Generous line-height (1.5-1.6)
- Professional color palette (avoid generic purples; consider navy, slate, or muted earth tones)
- Smooth scroll behavior
- Mobile-responsive breakpoints

### 4.2 Thinking Page

**Layout:**
- Hero section with page title and introduction
- Executive-level framing of thought process
- Grid layout for 4 Core Thinking Pillars:
  - Autonomy
  - Governance
  - Evaluation
  - Human-in-the-loop

**Visual Elements:**
- Icon or illustration for each pillar
- Card-based layout with hover effects
- Optional: Expandable sections for detailed explanations
- Diagram support for visual frameworks
- Callout boxes for key insights

**Design Requirements:**
- Consistent card styling with subtle shadows
- Prominent typography for pillar titles
- Visual hierarchy for scanning
- Whitespace between sections

### 4.3 Work Page

**Layout:**
- Hero section with page title and overview
- Grid of 3-5 curated case studies

**Case Card Components:**
- Title and brief description
- Context, Challenge, Approach, Outcome (summary view)
- "Read Full Case" or "View Details" CTA button
- Optional: Preview image or diagram thumbnail
- Tag system for categorization (ITSM, HR, Observability)

**Key Takeaway Section:**
- Full-width section at bottom
- Summarizes consistent frameworks and patterns
- Clean, editorial-style typography

**Design Requirements:**
- Card hover effects (subtle lift/shadow)
- Consistent grid spacing
- Responsive: 3 columns → 2 columns → 1 column
- Clear visual hierarchy

### 4.4 Drill-Down Case Pages

**Structure:**
- Hero section with case title and context
- Main content sections:
  - Challenge
  - Decision Points (table + optional diagram)
  - Approach
  - Outcome
  - Key Learnings

**Visual Elements:**
- Full-width sections with alternating backgrounds
- Inline diagrams/flowcharts
- Data tables with modern styling
- Pull quotes or callouts for key insights
- Navigation: "Back to Work" and "Next Case" links

**Design Requirements:**
- Long-form content styling with readable line-length
- Section breaks with visual dividers
- Diagram placeholders (SVG or image embeds)
- Consistent spacing rhythm

### 4.5 About / Credibility Page

**Layout:**
- Hero section with professional photo (optional)
- Executive bio section
- Experience highlights
- Optional: Timeline or career milestones

**Design Requirements:**
- Clean, editorial layout
- Focus on credibility and trust signals
- Minimal personal storytelling; emphasis on impact
- Professional photo styling (if included)

---

## 5. Design / UI Requirements

### Design System

**Typography:**
- **Display Font**: Distinctive, modern sans-serif (NOT Inter, Roboto, or Arial)
  - Options: DM Sans, Plus Jakarta Sans, Manrope, Epilogue, Cabinet Grotesk
- **Body Font**: Highly readable serif or refined sans-serif
  - Options: Crimson Pro, Source Serif, Lora (serif) or Inter Display, DM Sans (sans-serif)
- **Scale**: 
  - Hero headline: 56-72px (desktop), 36-48px (mobile)
  - Section titles: 32-40px
  - Body text: 16-18px
  - Line height: 1.6 for body, 1.2 for headlines

**Color Palette:**
- Primary: Professional navy, slate blue, or muted teal (avoid generic purple)
- Secondary: Complementary accent for CTAs
- Neutral: Gray scale (50, 100, 200...900)
- Background: Off-white or light warm gray (not pure white)
- Text: Near-black for primary, gray-700 for secondary

**Spacing System:**
- Base unit: 4px or 8px
- Section padding: 80-120px vertical (desktop), 48-64px (mobile)
- Component spacing: Consistent rhythm using Tailwind spacing scale

**Component Library:**

1. **Navigation Bar**
   - Sticky/fixed position
   - Logo + menu items + CTA button
   - Dropdown support for sub-menus
   - Mobile hamburger menu

2. **Hero Section**
   - Full viewport height or 70vh
   - Centered or left-aligned content
   - Large headline + subheadline + CTA buttons
   - Optional: Hero image or illustration

3. **Card Component**
   - Border or subtle shadow
   - Hover effects (lift + shadow increase)
   - Padding: 24-32px
   - Border radius: 8-12px

4. **Button Component**
   - Primary: Filled with accent color
   - Secondary: Outlined or ghost style
   - Hover states with smooth transitions
   - Padding: 12px 32px
   - Border radius: 6-8px

5. **Section Layouts**
   - Container max-width: 1200-1280px
   - Grid: 12-column system
   - Responsive breakpoints: sm, md, lg, xl

6. **Callout/Feature Boxes**
   - Background color variation
   - Border-left accent
   - Icon + content layout

7. **Logo Strip**
   - Grayscale logos
   - Even spacing
   - Responsive grid

### Animation & Interactions

**Micro-interactions:**
- Button hover: scale(1.02) + shadow increase
- Card hover: translateY(-4px) + shadow
- Link hover: color transition + underline animation

**Page Load Animations:**
- Fade-in for hero section
- Stagger animation for card grids (optional, CSS-only)
- Smooth scroll behavior

**Accessibility:**
- Prefers-reduced-motion support
- Focus states for keyboard navigation
- Sufficient color contrast (WCAG AA)

---

## 6. Technical Requirements

### Core Stack
- **Static Site Generator**: Hugo (v0.120+)
- **CSS Framework**: Tailwind CSS v3+
- **Hosting**: GitHub Pages
- **Version Control**: GitHub repository
- **CI/CD**: GitHub Actions for automated deployment

### Project Structure
```
my-portfolio/
├── config.toml (or hugo.toml)
├── content/
│   ├── _index.md (home page)
│   ├── thinking.md
│   ├── work/
│   │   ├── _index.md
│   │   ├── case-helixgpt.md
│   │   ├── case-hr-automation.md
│   │   └── case-pos.md
│   └── about.md
├── layouts/
│   ├── _default/
│   │   ├── baseof.html
│   │   ├── single.html
│   │   └── list.html
│   ├── partials/
│   │   ├── header.html
│   │   ├── footer.html
│   │   ├── hero.html
│   │   └── card.html
│   └── index.html (home page template)
├── static/
│   ├── images/
│   ├── diagrams/
│   └── css/ (compiled Tailwind)
├── assets/
│   └── css/
│       └── main.css (Tailwind source)
├── tailwind.config.js
├── package.json
└── .github/
    └── workflows/
        └── deploy.yml
```

### Content Front Matter (Example)
```yaml
---
title: "HelixGPT Multi-Agent System"
date: 2025-01-15
draft: false
category: "ITSM"
summary: "Brief summary for card display"
image: "/images/helixgpt-hero.jpg"
tags: ["AI Agents", "ITSM", "Automation"]
---
```

### Tailwind Configuration
- Custom color palette
- Custom font families
- Extended spacing scale
- Custom container widths
- Plugin for typography (prose classes)

### GitHub Actions Workflow
```yaml
name: Deploy Hugo site to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

jobs:
  deploy:
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
      - name: Build
        run: hugo --minify
      - name: Deploy
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./public
```

### SEO & Metadata
- Open Graph tags for social sharing
- Twitter Card meta tags
- Structured data (JSON-LD) for person/organization
- Sitemap generation (Hugo built-in)
- robots.txt configuration

---

## 7. Functional Requirements

### FR-01: Homepage Hero Section
**Description**: Display professional positioning statement with modern design
**Acceptance Criteria**:
- Large, readable headline (56-72px on desktop)
- Subheadline explaining value proposition
- Two CTA buttons with hover states
- Optional hero image with proper aspect ratio
- Responsive layout for mobile/tablet/desktop

### FR-02: Navigation Menu
**Description**: Sticky navigation accessible on all pages
**Acceptance Criteria**:
- Fixed position on scroll
- Logo/name on left
- Menu items: Home, Thinking, Work, About
- Mobile hamburger menu (< 768px)
- Smooth scroll to sections
- Active state indication

### FR-03: Thinking Page Pillars
**Description**: Present 4 core thinking pillars with visual hierarchy
**Acceptance Criteria**:
- Grid layout: 2x2 on desktop, 1x4 on mobile
- Each pillar card contains: icon/visual, title, description
- Optional expandable sections
- Consistent card styling with hover effects

### FR-04: Work Page Case Listing
**Description**: Display curated case studies in card format
**Acceptance Criteria**:
- Responsive grid: 3 columns (desktop) → 1 column (mobile)
- Each card shows: title, summary, category tag, CTA button
- Hover effects on cards
- Link to individual case pages
- Filter/sort by category (optional future enhancement)

### FR-05: Case Drill-Down Pages
**Description**: Detailed case study with structured sections
**Acceptance Criteria**:
- Hero section with case title and context
- Sections: Challenge, Approach, Decision Points, Outcome, Learnings
- Support for inline diagrams and tables
- Navigation to previous/next case
- "Back to Work" link
- Consistent typography and spacing

### FR-06: Logo Strip / Social Proof
**Description**: Display credibility through organization logos
**Acceptance Criteria**:
- Grayscale logo images
- Responsive grid (5-6 on desktop, 2-3 on mobile)
- Even spacing and alignment
- Optional: Subtle animation on scroll

### FR-07: Responsive Design
**Description**: Optimize for all device sizes
**Acceptance Criteria**:
- Breakpoints: sm (640px), md (768px), lg (1024px), xl (1280px)
- Touch-friendly buttons on mobile (min 44x44px)
- Readable text sizes on mobile (min 16px body)
- No horizontal scroll
- Test on: iPhone, Android, iPad, desktop

### FR-08: Markdown Content Authoring
**Description**: All content editable via Markdown files
**Acceptance Criteria**:
- Front matter for metadata
- Standard Markdown syntax support
- Shortcodes for special components (callouts, diagrams)
- Image embedding support
- Code block syntax highlighting (optional)

---

## 8. Non-Functional Requirements

### NFR-01: Performance
- **Target**: Lighthouse Performance score ≥ 90
- **Measures**:
  - First Contentful Paint (FCP) < 1.8s
  - Largest Contentful Paint (LCP) < 2.5s
  - Total Blocking Time (TBT) < 200ms
  - Cumulative Layout Shift (CLS) < 0.1
- **Implementation**:
  - Image optimization (WebP format, lazy loading)
  - Minified CSS/JS
  - Critical CSS inlining
  - Font preloading

### NFR-02: Accessibility
- **Target**: WCAG 2.1 Level AA compliance
- **Requirements**:
  - Color contrast ratio ≥ 4.5:1 for normal text
  - Keyboard navigation support
  - Focus indicators visible
  - ARIA labels where appropriate
  - Alt text for all images
  - Semantic HTML structure
  - Screen reader tested

### NFR-03: SEO
- **Requirements**:
  - Semantic HTML5 structure
  - Proper heading hierarchy (H1 → H6)
  - Meta descriptions for all pages
  - Open Graph and Twitter Card tags
  - Sitemap.xml generation
  - Mobile-friendly (passes Google Mobile-Friendly Test)
  - Fast page load times

### NFR-04: Maintainability
- **Requirements**:
  - Clear documentation in README
  - Consistent code formatting
  - Reusable Hugo partials/components
  - CSS organized by component
  - Easy to add new case studies (single Markdown file)
  - Version controlled with clear commit messages

### NFR-05: Security
- **Requirements**:
  - HTTPS enforced (GitHub Pages default)
  - No sensitive data in repository
  - Content Security Policy headers (via Netlify or Cloudflare, optional)
  - No external scripts except necessary CDN fonts

### NFR-06: Browser Compatibility
- **Target Browsers**:
  - Chrome/Edge (last 2 versions)
  - Firefox (last 2 versions)
  - Safari (last 2 versions)
  - Mobile Safari (iOS 14+)
  - Chrome Mobile (Android 10+)

---

## 9. Design Assets & Resources

### Required Assets
1. **Professional photo** (optional for hero or about page)
   - Format: JPG or WebP
   - Dimensions: 1200x800px minimum
   - Professional, high-quality image

2. **Company/Organization logos** (for social proof section)
   - Format: SVG or PNG
   - Grayscale or single-color
   - Transparent background

3. **Diagrams/Flowcharts** (for case studies)
   - Format: SVG (preferred) or PNG
   - Clear, readable at various sizes
   - Consistent styling

4. **Icons** (for thinking pillars, features)
   - Source: Heroicons, Lucide, or custom SVG
   - Consistent style across site

### Typography Resources
- **Google Fonts** (free, fast CDN)
- **Bunny Fonts** (privacy-friendly alternative)
- Custom font hosting via Hugo static folder

### Image Optimization
- Use Hugo's image processing for automatic resizing
- WebP format with JPEG fallback
- Lazy loading for below-fold images
- Appropriate alt text for accessibility

---

## 10. Development Phases

### Phase 1: Foundation (Week 1)
- [ ] Hugo project initialization
- [ ] Tailwind CSS configuration
- [ ] Base layout and navigation
- [ ] Typography and color system
- [ ] Component library (buttons, cards, hero)

### Phase 2: Core Pages (Week 2)
- [ ] Home page with hero and sections
- [ ] Thinking page with pillars
- [ ] Work page with case cards
- [ ] About page

### Phase 3: Case Studies (Week 3)
- [ ] Case drill-down template
- [ ] Populate 3-5 case studies
- [ ] Diagram integration
- [ ] Inter-page navigation

### Phase 4: Polish & Deploy (Week 4)
- [ ] Responsive testing and refinement
- [ ] Performance optimization
- [ ] Accessibility audit
- [ ] SEO metadata
- [ ] GitHub Actions workflow
- [ ] Deploy to GitHub Pages

---

## 11. Success Metrics

### Primary Success Criteria
1. **Executive Comprehension**: CIO/CTO/Founder can understand frameworks and judgment within 2-3 minutes of landing on site
2. **Visual Impact**: First impression communicates professionalism and modern design sensibility
3. **Content Accessibility**: Easy navigation to thinking frameworks and work examples

### Secondary Success Criteria
4. **Maintainability**: Owner can update content via Markdown and deploy in < 5 minutes
5. **Performance**: Lighthouse score ≥ 90 on all pages
6. **Mobile Experience**: Seamless experience on mobile devices (50%+ of traffic)

### Optional Metrics (Future)
7. Time on site and page views
8. Bounce rate from landing page
9. Feedback from peers/executive visitors
10. Contact form submissions (if added)

---

## 12. Future Enhancements (Post-Launch)

### Content Enhancements
- [ ] Blog/Notes section for continuous insights
- [ ] Case study filtering by domain (ITSM, HR, Observability)
- [ ] Speaking engagements or publications section
- [ ] Downloadable resume/CV

### Design Enhancements
- [ ] Light/Dark mode toggle
- [ ] Interactive diagrams with JavaScript
- [ ] Scroll-triggered animations (IntersectionObserver)
- [ ] Custom illustrations for thinking pillars

### Technical Enhancements
- [ ] Contact form with serverless function
- [ ] Search functionality (Algolia or Pagefind)
- [ ] Analytics integration (privacy-focused)
- [ ] RSS feed for blog content
- [ ] Progressive Web App (PWA) features

---

## 13. Handoff to Claude Code

### Development Approach
This website will be built using **Claude Code**, an agentic AI coding tool that can execute the entire development workflow.

### What to Provide to Claude Code
1. **This PRD** (complete specification)
2. **Existing Markdown content files** for all pages
3. **Design reference**: Observe.AI screenshot for visual style inspiration
4. **Asset files**: Professional photo, logos, diagrams (if available)

### Expected Workflow
1. Claude Code initializes Hugo + Tailwind project
2. Configures Tailwind with custom design system
3. Creates layout templates and partials
4. Implements component library
5. Integrates Markdown content
6. Builds responsive pages matching design spec
7. Sets up GitHub Actions deployment
8. Tests and optimizes performance
9. Delivers production-ready site with documentation

### Repository Structure
- Clear README with setup instructions
- Documentation for adding new content
- Component usage examples
- Deployment instructions
- Maintenance guidelines

---

## Appendix A: Example Page Layouts

### Home Page Wireframe
```
+------------------------------------------+
|  NAVIGATION BAR                          |
+------------------------------------------+
|                                          |
|  HERO SECTION (full viewport height)    |
|  - Large headline                        |
|  - Subheadline                           |
|  - CTA buttons                           |
|  - Hero image (right side)               |
|                                          |
+------------------------------------------+
|  VALUE PROPOSITION (3-column grid)       |
|  [Icon]  [Icon]  [Icon]                  |
|  Title   Title   Title                   |
|  Desc    Desc    Desc                    |
+------------------------------------------+
|  SOCIAL PROOF / LOGOS                    |
|  [Logo] [Logo] [Logo] [Logo] [Logo]      |
+------------------------------------------+
|  CALL-TO-ACTION SECTION                  |
|  Headline + CTA Button                   |
+------------------------------------------+
|  FOOTER                                  |
+------------------------------------------+
```

### Work Page Wireframe
```
+------------------------------------------+
|  NAVIGATION BAR                          |
+------------------------------------------+
|  HERO SECTION                            |
|  Page Title + Introduction               |
+------------------------------------------+
|  CASE STUDIES (3-column grid)            |
|  +------------+ +------------+ +-------+ |
|  | Case Card  | | Case Card  | | Case  | |
|  | - Title    | | - Title    | | Card  | |
|  | - Summary  | | - Summary  | |       | |
|  | - CTA      | | - CTA      | |       | |
|  +------------+ +------------+ +-------+ |
+------------------------------------------+
|  KEY TAKEAWAYS SECTION                   |
|  Summary text + patterns                 |
+------------------------------------------+
|  FOOTER                                  |
+------------------------------------------+
```

---

## Appendix B: Tailwind Config Example

```javascript
// tailwind.config.js
module.exports = {
  content: [
    './layouts/**/*.html',
    './content/**/*.md',
  ],
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#f0f9ff',
          // ... full scale
          900: '#0c4a6e',
        },
        accent: {
          // Your accent color scale
        },
      },
      fontFamily: {
        display: ['DM Sans', 'sans-serif'],
        body: ['Crimson Pro', 'serif'],
      },
      spacing: {
        '18': '4.5rem',
        '88': '22rem',
        '128': '32rem',
      },
      maxWidth: {
        '8xl': '88rem',
      },
    },
  },
  plugins: [
    require('@tailwindcss/typography'),
  ],
}
```

---

**END OF PRD**

This updated PRD provides comprehensive specifications for building a modern, professional portfolio website using Hugo + Tailwind + GitHub Pages, ready for implementation with Claude Code.