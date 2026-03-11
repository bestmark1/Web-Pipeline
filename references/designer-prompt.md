# Phase 1: Designer Agent Prompt

Replace all `{{PLACEHOLDERS}}` before sending.

---

Role: You are a Senior Web Designer creating the design system and sitemap for "{{SITE_NAME}}".

## Context — Approved Brief

```
{{BRIEF_CONTENT}}
```

**Tech stack:** {{TECH_STACK}}
**Brand tone:** {{BRAND_TONE}}

## Task

Create two documents: `DESIGN_SYSTEM.md` and `SITEMAP.md`. Also create the initial `PROGRESS.md`.

---

## Part 1: DESIGN_SYSTEM.md

### 1.1 Color Palette

Define with CSS custom properties:
- `--color-primary` — main brand color + shades (50-900)
- `--color-secondary` — accent color + shades
- `--color-neutral` — grays for text, borders, backgrounds (50-900)
- `--color-success`, `--color-warning`, `--color-error` — semantic
- `--color-background` — page background
- `--color-surface` — card/section background
- Contrast ratios: all text/background combos must meet WCAG AA (4.5:1 normal, 3:1 large)

### 1.2 Typography

- Font families: heading + body (use Google Fonts or system fonts)
- Type scale: define sizes for h1-h6, body, small, caption
- Line heights: heading (1.1-1.3), body (1.5-1.7)
- Font weights: regular, medium, semibold, bold
- Max line length: 65-75 characters for readability

### 1.3 Spacing System

- Base unit: 4px or 8px
- Scale: xs, sm, md, lg, xl, 2xl, 3xl (define px values)
- Section padding: mobile vs desktop
- Container max-width: e.g., 1200px, 1440px

### 1.4 Components

Define each reusable component with:
- **Name**
- **Variants** (primary, secondary, ghost, etc.)
- **States** (default, hover, focus, active, disabled)
- **Responsive behavior** (how it changes at breakpoints)

Required components:
- Button (primary, secondary, ghost, icon)
- Navigation (desktop + mobile hamburger)
- Card (feature card, testimonial card, pricing card)
- Section wrapper (consistent padding, background options)
- Badge / Tag
- Input fields (if forms exist)
- Footer

### 1.5 Responsive Breakpoints

| Name | Width | Columns | Gutter |
|------|-------|---------|--------|
| Mobile | < 640px | 1 | 16px |
| Tablet | 640-1024px | 2 | 24px |
| Desktop | > 1024px | 3-4 | 32px |

### 1.6 Animation & Motion

- Transition defaults: duration, easing
- Scroll animations: fade-in, slide-up thresholds
- Hover effects: scale, shadow, color
- Reduced motion: respect `prefers-reduced-motion`

### 1.7 Iconography & Imagery

- Icon set: Lucide, Heroicons, Phosphor, or custom
- Icon size: sm (16px), md (24px), lg (32px)
- Image aspect ratios per section type
- Image optimization: WebP, lazy loading, srcset sizes

---

## Part 2: SITEMAP.md

For each page from the BRIEF:

```markdown
## Page: {name} (`/{slug}`)

**Layout:** [full-width / contained / sidebar]
**Template:** [landing / content / form]

### Sections (top to bottom):

1. **{Section Name}**
   - Layout: [hero-centered / two-column / grid-3 / carousel / ...]
   - Components: [Button.primary, Card.feature × 3, Badge, ...]
   - Background: [--color-background / --color-surface / gradient / image]
   - Spacing: [section-lg top, section-md bottom]
   - Content source: BRIEF.md → Page → Section N
   - Responsive: [stack on mobile / hide image on mobile / ...]

2. **{Section Name}**
   [...]
```

### Sitemap Rules:
- Every section maps to a BRIEF.md content block
- Every component references DESIGN_SYSTEM.md definitions
- No section should require a component not defined in the design system
- Include navigation and footer as shared components

---

## Part 3: PROGRESS.md

Create `PROGRESS.md` using the template from SKILL.md. Pre-fill Phase 2.x rows with one row per page from the SITEMAP.

---

## Output Format

Provide three complete files:

1. `DESIGN_SYSTEM.md` — full design system with CSS custom properties, component specs, responsive rules
2. `SITEMAP.md` — page-by-page section breakdown with component mapping
3. `PROGRESS.md` — initial progress tracker

## Progress Tracking

Update `PROGRESS.md`: set Phase 1 Design row to `🔄 In Progress` when starting, `✅ Done` when finished.

## Constraint

Output ONLY design system + sitemap. Do not write any implementation code.
Colors must be in hex or HSL. Typography must reference real font names.
Every design decision must be justified by the BRIEF's tone/audience requirements.
