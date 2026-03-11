# Web Pipeline

Claude Code skill that orchestrates 6 specialized AI agents through a structured website/landing page creation workflow with 4 approval gates.

## Pipeline Flow

```
[Researcher] → [Content Strategist] → BRIEF.md → ⛔ USER APPROVAL
  → [Designer] → DESIGN_SYSTEM.md + SITEMAP.md → ⛔ USER APPROVAL
    → loop per page:
        [Frontend Dev] → code
        → [SEO Reviewer] ‖ [A11y Reviewer]
        → both APPROVE → next page
    → [QA Agent] → Lighthouse + responsive
        → QA PASS → PR → ⛔ USER REVIEWS
```

## Agents

| # | Agent | Phase | Output |
|---|-------|-------|--------|
| 1 | **Researcher** | 0a | Market research, competitor analysis, audience personas, SEO keywords |
| 2 | **Content Strategist** | 0b | `BRIEF.md` — page-by-page content plan with real copy |
| 3 | **Designer** | 1 | `DESIGN_SYSTEM.md` + `SITEMAP.md` — colors, typography, components, layouts |
| 4 | **Frontend Dev** | 2 | Code per page with self-review loop |
| 5 | **SEO Reviewer** | 2 | Technical SEO, meta tags, structured data, keyword optimization |
| 6 | **A11y Reviewer** | 2 | WCAG 2.1 AA compliance, contrast, keyboard nav, screen reader |
| 7 | **QA Agent** | 3 | Lighthouse audit, responsive check, content verification |

## Approval Gates

1. **Brief approved** — user reviews content strategy before design starts
2. **Design approved** — user reviews design system before coding starts
3. **Review gate** — both SEO + A11y reviewers must APPROVE each page
4. **QA gate** — Lighthouse ≥ 90, all checks pass before PR

## Features

- **Stack-agnostic** — Next.js, Astro, Hugo, plain HTML/CSS
- **PROGRESS.md** — visual pipeline status auto-updated by every agent
- **Auto-commits** — `[phase-N]` prefixed, specific files only
- **Feature branches** — `feature/{slug}`, PR at the end
- **STRICT_MODE** — set `false` for rapid prototyping (review gates become advisory)
- **Recovery procedures** — structured flows for rejected briefs, stuck review loops, QA failures

## File Structure

```
web-pipeline/
├── SKILL.md                          # Main orchestration (291 lines)
└── references/
    ├── researcher-prompt.md          # Market research agent
    ├── content-strategist-prompt.md  # Content brief agent
    ├── designer-prompt.md            # Design system + sitemap agent
    ├── frontend-dev-prompt.md        # Coding agent with self-review
    ├── reviewer-seo-prompt.md        # SEO review agent
    ├── reviewer-a11y-prompt.md       # Accessibility review agent
    └── qa-prompt.md                  # QA validation agent
```

## Installation

Copy to your Claude Code skills directory:

```bash
cp -r . ~/.claude/skills/web-pipeline/
```

## Usage

Tell Claude Code: *"build a landing page for..."* or *"web pipeline"* — the skill triggers automatically.

## Related

- [Phased Engineering Pipeline](https://github.com/bestmark1/Phased-Engineering-Pipeline) — for full-stack apps with backend logic, databases, APIs
