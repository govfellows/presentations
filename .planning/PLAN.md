# Innovation Fellowship Library — Site Restructure Plan

> **Status:** Ready for execution
> **Project:** `/Users/slate/presentations/`
> **Deployed at:** https://vanderoffice.github.io/presentations/
> **Repo:** `vanderoffice/presentations` (GitHub Pages)

---

## Context

The Governor's Innovation Fellowship produces presentations that serve different purposes — executive briefings for agency leaders and the Governor's Office, AI training curricula for state workers, and operational guides for future fellowship cohorts. Today, these all live in a single flat directory with a vertical card list as the landing page (`index.html`, 318 lines). The site needs to scale to 20-30+ presentations organized by purpose, not chronology.

### What Exists Today

```
presentations/
├── index.html                                          (landing page — flat card list)
├── ca-enterprise-modernization-govoffice-2026-01.html  (26+35 slides, Governor's Office)
├── ca-enterprise-modernization-appendix-2026-01.html   (technical appendix)
├── rag-quality-assurance-2026-01.html                  (16 slides, RAG QA)
├── claude-code-deployment-swrcb-2026-01-24.html        (14 slides, SWRCB)
├── tea-cabinet-briefing-2026-01.html                   (15 slides, TEA framework)
└── corrections-digital-transformation-2026-01.html     (13 slides, CDCR)
```

- **Framework:** Reveal.js v5.1.0 (CDN)
- **Theme:** California Modern (dark navy `#08080f`, gold `#d4a04a`, blue `#4a9eff`)
- **Fonts:** Inter (Google Fonts), JetBrains Mono for code
- **Build system:** None — raw static HTML, all CSS inline, all JS inline
- **Deployment:** Git push → GitHub Pages (no CI/CD)

### Design System Reference (California Modern)

```css
:root {
  --bg-primary: #08080f;
  --bg-secondary: #0e0e18;
  --bg-elevated: #1a1a28;
  --text-primary: #f2f2f8;
  --text-secondary: #a5a5b8;
  --text-muted: #65657a;
  --accent-blue: #4a9eff;
  --accent-gold: #d4a04a;
  --accent-teal: #4a9a7a;
  --accent-burgundy: #a85454;
}
/* Font: Inter 400-700, -apple-system fallback */
/* Cards: bg-secondary with bg-elevated border, gold left-border, 12px radius */
/* Hover: accent-blue border, translateY(-2px), blue box-shadow */
/* Tags: pill-shaped, colored bg with matching text per category */
/* Gold underline on h1 (::after pseudo-element, 80px × 3px) */
```

### Current `index.html` Card HTML Pattern

```html
<a href="[filename].html" class="presentation-card">
  <div class="card-header">
    <span class="card-title">Title<span class="badge-new">New</span></span>
    <div class="card-meta">
      <span class="card-slides">N slides</span>
      <span class="card-dates">Created Jan XX</span>
    </div>
  </div>
  <p class="card-description">Description text.</p>
  <div class="card-tags">
    <span class="tag government">Government</span>
    <span class="tag technical">Technical</span>
  </div>
</a>
```

---

## Architecture Decision

**Multi-page static site with three content categories.** Each category gets its own index page, plus a redesigned hub. Presentation HTML files move to a `decks/` subdirectory. No build system, no framework — just organized HTML.

### Category Design Principle

Categories are defined by **what the content does**, not what it's about:

| Category | Function | What belongs here |
|----------|----------|-------------------|
| **Briefings** | Informs external audiences | Executive explainers, governance proposals, agency overviews, progress reports, policy frameworks, stakeholder updates — anything presented to people outside the Fellowship |
| **Training** | Teaches skills in sequence | AI courses, OCM change management, compliance training, tool adoption guides — anything where order matters and a learner tracks progress |
| **FellowOps** | Runs the Fellowship internally | Onboarding, sprint methodology, agency engagement playbooks, cohort transitions, lessons learned — content for fellows and ODI staff |

Subtypes within a category are handled by **tags** (e.g., `governance`, `explainer`, `proposal`, `agency-overview`), not by creating more categories. Tags can be added and renamed without restructuring the site.

### Target Structure

```
presentations/
├── .planning/
│   └── PLAN.md                             ← this file
├── index.html                              ← REDESIGNED hub page
├── briefings/
│   └── index.html                          ← Briefings catalog with tag filters
├── training/
│   └── index.html                          ← Training curriculum (sequenced, progress-tracked)
├── fellowops/
│   └── index.html                          ← Fellowship operations & onboarding
└── decks/
    ├── ca-enterprise-modernization-govoffice-2026-01.html
    ├── ca-enterprise-modernization-appendix-2026-01.html
    ├── rag-quality-assurance-2026-01.html
    ├── claude-code-deployment-swrcb-2026-01-24.html
    ├── tea-cabinet-briefing-2026-01.html
    └── corrections-digital-transformation-2026-01.html
```

### Where Existing Decks Land

| Deck | Category | Tags | Rationale |
|------|----------|------|-----------|
| CA Enterprise Modernization Plan | **Briefings** | `governance`, `executive` | Informs Governor's Office about IT modernization landscape |
| CA Enterprise Modernization Appendix | **Briefings** | `governance`, `technical` | Detailed supporting material for the above |
| TEA Cabinet Briefing | **Briefings** | `governance`, `executive` | Proposes competence standards — informing cabinet of a framework |
| Corrections Digital Transformation | **Briefings** | `agency-overview`, `cdcr` | Informs stakeholders about CDCR modernization opportunity |
| Claude Code Deployment at SWRCB | **Briefings** | `technology`, `swrcb` | Executive briefing on deploying AI coding tools |
| RAG Quality Assurance | **Training** | `ai`, `technical` | Teaches best practices — skill-building content |

Note: Claude Code Deployment could also appear in Training as part of the AI course sequence. A deck can be referenced from multiple category pages — the HTML file lives in `decks/` once, but cards can link to it from wherever it's relevant.

---

## Implementation Steps

### Step 1: Create Directory Structure & Move Decks

Create the directory layout and move existing presentation HTML files into `decks/`.

```bash
cd /Users/slate/presentations
mkdir -p decks briefings training fellowops .planning
```

Move all presentation HTML files (NOT index.html) into `decks/`:

```bash
mv ca-enterprise-modernization-govoffice-2026-01.html decks/
mv ca-enterprise-modernization-appendix-2026-01.html decks/
mv rag-quality-assurance-2026-01.html decks/
mv claude-code-deployment-swrcb-2026-01-24.html decks/
mv tea-cabinet-briefing-2026-01.html decks/
mv corrections-digital-transformation-2026-01.html decks/
```

**IMPORTANT — Link updates inside the decks:** Each deck file is self-contained (CDN resources, inline CSS/JS). No internal cross-links to update. The only links that break are in `index.html`, which gets rewritten in Step 3.

**Verify:** `ls decks/` should show 6 HTML files. `ls *.html` in root should show only `index.html`.

---

### Step 2: Create Category Index Pages

Build three category pages. All use the California Modern theme but each serves a different purpose with category-appropriate features.

#### 2a: `briefings/index.html` — Briefings

**Purpose:** Catalog of all external-facing presentations — executive briefings, governance proposals, agency overviews, technology explainers.

**Layout:** Back-link to hub → page title + description → tag filter bar → card grid

**Page elements:**
- **Back link:** `← Back to Library` linking to `../`
- **Title:** "Briefings"
- **Subtitle:** "Executive briefings, governance frameworks, and agency overviews for California state government leaders and stakeholders."
- **Tag filter bar:** Clickable tag pills that filter the cards below. Tags: `governance`, `executive`, `technology`, `agency-overview`, `technical`. Click a tag to show only matching cards. Click again (or "All") to clear filter.
- **Card grid:** 1 column on mobile, 2 columns on desktop (>768px)

**Tag filter implementation (vanilla JS):**
```javascript
// Each card has data-tags="governance executive" attribute
// Click tag pill → toggle .active on pill, hide cards that don't match
// "All" pill is default active, shows everything
// Multiple tags = OR logic (show card if it has ANY active tag)
document.querySelectorAll('.filter-tag').forEach(tag => {
  tag.addEventListener('click', () => {
    // toggle active state, filter cards by data-tags
  });
});
```

**Cards to include (5 existing decks):**

1. **California Enterprise Modernization Plan**
   - Link: `../decks/ca-enterprise-modernization-govoffice-2026-01.html`
   - Meta: 26 + 35 slides · Jan 2026
   - Description: Governor's Office briefing on the comprehensive state IT modernization strategy. Covers E3 accountability model, Technical Executive Assignment framework, data governance, $100M Breakthrough Fund, and procurement reform.
   - Secondary link: "View Appendix →" → `../decks/ca-enterprise-modernization-appendix-2026-01.html`
   - Tags: `governance`, `executive`

2. **Technical Executive Standards Initiative**
   - Link: `../decks/tea-cabinet-briefing-2026-01.html`
   - Meta: 15 slides · Jan 2026
   - Description: Cabinet briefing on the TEA framework. Establishes verified competence requirements for CIO, CISO, CDO, and CTO positions in California state government.
   - Tags: `governance`, `executive`

3. **Claude Code Deployment at SWRCB**
   - Link: `../decks/claude-code-deployment-swrcb-2026-01-24.html`
   - Meta: 14 slides · Jan 2026
   - Description: Executive briefing for deploying AI coding assistants in California state government. Covers compliance requirements, risk classification, technical controls, and phased implementation.
   - Tags: `technology`, `executive`

4. **Digital Transformation in Corrections**
   - Link: `../decks/corrections-digital-transformation-2026-01.html`
   - Meta: 13 slides · Jan 2026
   - Description: Strategic framework for modernizing correctional facility operations through secure technology adoption, AI-assisted case management, and data-driven decision making.
   - Tags: `agency-overview`, `technical`

**Card HTML pattern for briefings:**
```html
<a href="../decks/[filename].html" class="presentation-card" data-tags="governance executive">
  <div class="card-header">
    <span class="card-title">Title</span>
    <div class="card-meta">
      <span class="card-slides">N slides</span>
      <span class="card-dates">Jan 2026</span>
    </div>
  </div>
  <p class="card-description">Description.</p>
  <div class="card-tags">
    <span class="tag governance">Governance</span>
    <span class="tag executive">Executive</span>
  </div>
</a>
```

**Tag color assignments:**
```css
.tag.governance  { background: rgba(168, 84, 84, 0.15); color: #c87070; }
.tag.executive   { background: rgba(212, 160, 74, 0.15); color: var(--accent-gold); }
.tag.technology  { background: rgba(74, 154, 122, 0.15); color: var(--accent-teal); }
.tag.agency-overview { background: rgba(74, 158, 255, 0.15); color: var(--accent-blue); }
.tag.technical   { background: rgba(74, 154, 122, 0.15); color: var(--accent-teal); }
```

---

#### 2b: `training/index.html` — Training

**Purpose:** Sequenced learning paths. The AI course lives here, and future courses (OCM, compliance, etc.) can be added as separate sections.

**Layout:** Back-link → page title + description → course sections (each with its own header, description, and numbered module list)

**Page elements:**
- **Back link:** `← Back to Library` linking to `../`
- **Title:** "Training"
- **Subtitle:** "Structured learning paths for California state employees. Complete modules in order to build practical AI and technology skills."

**Course section: "AI for California Government"**
- **Course description:** "A 6-module course designed for California state employees with 10+ years of experience and spreadsheet-level technical skills. Learn to use AI tools effectively, responsibly, and in compliance with state policy."
- **Progress bar:** Visual bar showing completed/total modules
- **Numbered module list:** Each module is a card with a number, title, description, slide count, and status

**Modules for AI course:**
1. **AI Foundations for California Government** — *Coming Soon*
   - What AI is, how it works, and why it matters for state government
2. **Search, Research & Verification with AI** — *Coming Soon*
   - Using AI tools for research while maintaining accuracy and trust
3. **Prompt Engineering for Government Work** — *Coming Soon*
   - Writing effective prompts for policy analysis, drafting, and decision support
4. **Claude Code Deployment at SWRCB** — *Available*
   - Link: `../decks/claude-code-deployment-swrcb-2026-01-24.html`
   - 14 slides
5. **Quality Assurance for RAG Knowledge Bases** — *Available*
   - Link: `../decks/rag-quality-assurance-2026-01.html`
   - 16 slides
6. **The Agentic Future: AI in Government Operations** — *Coming Soon*
   - Where AI is headed and what it means for California state services

**Progress tracking implementation (vanilla JS):**
```javascript
const STORAGE_KEY = 'training-progress';

function getProgress() {
  return JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]');
}

function toggleComplete(slug) {
  let progress = getProgress();
  if (progress.includes(slug)) {
    progress = progress.filter(s => s !== slug);
  } else {
    progress.push(slug);
  }
  localStorage.setItem(STORAGE_KEY, JSON.stringify(progress));
  updateUI();
}

function updateUI() {
  const progress = getProgress();
  const total = document.querySelectorAll('.module-card:not(.coming-soon)').length;
  const completed = progress.length;
  // Update progress bar width
  // Update checkmark icons on completed modules
}
```

**Module card HTML patterns:**

Available module:
```html
<div class="module-card" data-slug="claude-code-deployment">
  <span class="module-number">4</span>
  <div class="module-content">
    <h3><a href="../decks/claude-code-deployment-swrcb-2026-01-24.html">Claude Code Deployment at SWRCB</a></h3>
    <p class="module-description">Executive briefing for deploying AI coding assistants in California state government.</p>
    <span class="module-meta">14 slides</span>
  </div>
  <button class="module-complete-btn" onclick="toggleComplete('claude-code-deployment')">
    Mark Complete
  </button>
</div>
```

Coming soon module:
```html
<div class="module-card coming-soon">
  <span class="module-number">1</span>
  <div class="module-content">
    <h3>AI Foundations for California Government</h3>
    <p class="module-description">What AI is, how it works, and why it matters for state government.</p>
    <span class="module-meta coming-soon-label">Coming Soon</span>
  </div>
</div>
```

**Coming soon styling:** Reduced opacity (0.6), no hover effect, muted text. Do NOT use `pointer-events: none`.

**Future courses** (OCM, compliance, etc.) would be added as additional sections on this same page, each with their own header, description, and module list. The page structure supports multiple courses without restructuring.

---

#### 2c: `fellowops/index.html` — FellowOps

**Purpose:** Internal resources for running the Governor's Innovation Fellowship program. Onboarding, methodology, institutional memory.

**Layout:** Back-link → page title + description → "Start Here" callout → section stubs

**This is a placeholder page.** Content will be built out over time. The structure communicates the vision and gives future authors clear slots to fill.

**Page elements:**
- **Back link:** `← Back to Library` linking to `../`
- **Title:** "FellowOps"
- **Subtitle:** "Resources for Governor's Innovation Fellows, cohort leads, and ODI program staff. Onboarding guides, methodology documentation, and institutional knowledge from previous cohorts."

**Sections to stub out with visible structure + placeholder text:**

1. **Start Here** (prominent callout box at top, gold-bordered)
   - "New to the Governor's Innovation Fellowship? Start with these essentials."
   - Placeholder cards: "Fellowship Overview" (Coming Soon), "Your First Two Weeks" (Coming Soon)

2. **Methodology & Coordination**
   - "How we run sprints, coordinate across agencies, and ship deliverables."
   - Placeholder cards: "Sprint Methodology" (Coming Soon), "Agency Engagement Playbook" (Coming Soon), "ODI Coordination Patterns" (Coming Soon)

3. **Cohort Transitions**
   - "Guides for transitioning between fellowship cohorts."
   - Placeholder cards: "Handoff Playbook" (Coming Soon), "Senior Fellow Roles" (Coming Soon)

4. **Lessons Learned**
   - "Retrospectives and case studies from previous cohorts."
   - Placeholder cards: "Cohort 1 Retrospective" (Coming Soon)

**Placeholder card HTML:**
```html
<div class="resource-card coming-soon">
  <h3>Sprint Methodology</h3>
  <p class="resource-description">How we structure sprints, standups, and demos across distributed teams.</p>
  <span class="coming-soon-label">Coming Soon</span>
</div>
```

Each section should have a visible header and at least one placeholder card. Empty sections with just a header and "Coming Soon" text are fine — they communicate intent and make it obvious where new content should go.

---

### Step 3: Redesign Hub Page (`index.html`)

Replace the current flat card list with a structured hub. This is the front door to the library.

**New layout:**

```
┌──────────────────────────────────────────────────────┐
│                                                       │
│  🏛️ Governor's Innovation Fellowship                  │
│     ─── (gold accent bar) ───                         │
│  Knowledge & Briefing Library                         │
│  Resources for California's government                │
│  modernization initiative                             │
│                                                       │
├──────────────────────────────────────────────────────┤
│                                                       │
│  ┌───────────────┐ ┌───────────────┐ ┌─────────────┐ │
│  │ 🏛️ Briefings  │ │ 📚 Training   │ │ ⚙️ FellowOps│ │
│  │               │ │               │ │              │ │
│  │ Executive     │ │ Structured    │ │ Onboarding,  │ │
│  │ briefings,    │ │ learning      │ │ methodology  │ │
│  │ governance    │ │ paths for     │ │ & lessons    │ │
│  │ frameworks,   │ │ state         │ │ for current  │ │
│  │ and agency    │ │ employees.    │ │ and future   │ │
│  │ overviews.    │ │               │ │ cohorts.     │ │
│  │               │ │ 1 course ·    │ │              │ │
│  │ 4 briefings   │ │ 2 of 6 ready  │ │ Coming Soon  │ │
│  │ [Browse →]    │ │ [Browse →]    │ │ [Browse →]   │ │
│  └───────────────┘ └───────────────┘ └─────────────┘ │
│                                                       │
│  ── Recently Added ────────────────────────────────── │
│                                                       │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────┐  │
│  │ CA Enterprise│ │ TEA Cabinet  │ │ Claude Code  │  │
│  │ Modern...    │ │ Briefing     │ │ Deployment   │  │
│  │ Jan 26       │ │ Jan 25       │ │ Jan 25       │  │
│  │ [Briefings]  │ │ [Briefings]  │ │ [Briefings]  │  │
│  └──────────────┘ └──────────────┘ └──────────────┘  │
│                                                       │
├──────────────────────────────────────────────────────┤
│  View on GitHub                                       │
└──────────────────────────────────────────────────────┘
```

**Key design decisions:**
- **3-column category grid** on desktop, stacks to single column on mobile (≤600px)
- Category cards are the primary navigation — larger and more prominent than deck cards (~200px min-height)
- Each category card shows: emoji icon, title, 2-3 line description, count of available items, "Browse →" link
- **"Recently Added" section** below the grid shows the 3 newest decks as compact cards (title + date + category tag). Keeps the hub feeling alive for returning visitors.
- **Title:** "Governor's Innovation Fellowship" with gold accent bar, subtitle "Knowledge & Briefing Library"
- Same California Modern theme, fonts, color palette as existing site
- Remove "Use arrow keys" footer instruction (that's for individual decks, not the hub)

**Category card component:**
```html
<a href="briefings/" class="category-card">
  <div class="category-icon">🏛️</div>
  <h2 class="category-title">Briefings</h2>
  <p class="category-description">
    Executive briefings, governance frameworks, and agency overviews
    for California state government leaders and stakeholders.
  </p>
  <div class="category-footer">
    <span class="category-count">4 briefings</span>
    <span class="category-link">Browse →</span>
  </div>
</a>
```

**Compact "recently added" card:**
```html
<a href="decks/[filename].html" class="recent-card">
  <h3 class="recent-title">California Enterprise Modernization Plan</h3>
  <div class="recent-meta">
    <span class="recent-date">Jan 26, 2026</span>
    <span class="tag governance">Briefings</span>
  </div>
</a>
```

**Category card styling guidance:**
- ~200px min-height, flex column layout
- Gold left-border accent (carries over from existing card design)
- Same hover treatment: `translateY(-2px)`, blue border, blue box-shadow
- Emoji icon: ~2rem size
- Footer pinned to bottom of card with `margin-top: auto`

**Responsive breakpoints:**
- Desktop (>900px): 3-column grid for categories, 3-column for recent
- Tablet (601-900px): 3-column grid for categories (narrower), 2-column for recent
- Mobile (≤600px): single column everything

---

### Step 4: Verify & Test

1. **All links work:** Every card on every page must resolve correctly. Relative paths from category pages to decks use `../decks/filename.html`. Hub links to categories use `briefings/`, `training/`, `fellowops/`.
2. **GitHub Pages routing:** Subdirectory `index.html` files are served at `/presentations/briefings/`, `/presentations/training/`, etc. This works by default with GitHub Pages — no configuration needed.
3. **Back navigation:** Every category page has `← Back to Library` linking to `../`.
4. **Mobile responsive:** All pages at 375px width (iPhone SE). Cards stack, text readable, no horizontal scroll.
5. **Tag filtering (Briefings):** Click a tag filter pill, cards filter. Click "All" to reset. Verify with 2+ different tags.
6. **Progress tracking (Training):** Mark a module complete, refresh the page — checkmark and progress bar persist. Mark it incomplete (toggle), refresh — cleared.
7. **Coming soon states:** FellowOps page renders with placeholder sections. Training "Coming Soon" modules show dimmed but visible.

---

### Step 5: Git Commit & Deploy

```bash
cd /Users/slate/presentations
git add -A
git commit -m "Restructure site into Knowledge & Briefing Library

Reorganize from flat card list to multi-page library with three
content categories: Briefings (external-facing), Training (sequenced
learning), FellowOps (internal fellowship resources). Move all
presentation HTML into decks/ subdirectory. New hub page with
category grid and recently added section."

git push origin main
```

Verify deployment at https://vanderoffice.github.io/presentations/ after push (GitHub Pages typically deploys within 1-2 minutes).

---

## Design Notes

### Shared Page Shell

All category pages follow the same structural shell. Only the content section varies:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>[Category] | Innovation Fellowship Library</title>
  <link rel="icon" href="data:image/svg+xml,...">
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    /* California Modern variables + base styles (same as current index.html) */
    /* Category-specific styles */
  </style>
</head>
<body>
  <div class="container">
    <nav class="back-nav">
      <a href="../">← Back to Library</a>
    </nav>
    <header>
      <h1>[Category Title]</h1>
      <p class="subtitle">[Category description]</p>
    </header>

    <!-- Category-specific content -->

    <footer>
      <a href="https://github.com/vanderoffice/presentations">View on GitHub</a>
    </footer>
  </div>
</body>
</html>
```

### Back Nav Styling
```css
.back-nav {
  margin-bottom: 2rem;
}
.back-nav a {
  color: var(--accent-blue);
  text-decoration: none;
  font-size: 0.9rem;
}
.back-nav a:hover {
  text-decoration: underline;
}
```

---

## What This Plan Does NOT Cover

- **Creating new presentation content** (new slide decks) — that's separate work
- **Build system / static site generator** — not needed at this scale
- **Authentication or user accounts** — localStorage progress is anonymous
- **Shared CSS extraction** — keep styles inline for now (each page is self-contained like the decks)
- **The `deck` skill pipeline** — this plan is about the site structure, not how decks are authored

---

## Execution Summary

- **Working directory:** `/Users/slate/presentations/`
- **Total new files:** 4 HTML files (hub rewrite + 3 category pages)
- **Files moved:** 6 presentation HTMLs from root to `decks/`
- **Directories created:** `decks/`, `briefings/`, `training/`, `fellowops/`
- **Files deleted:** None (index.html is rewritten in-place)
- **No npm, no build, no dependencies** — just HTML/CSS/JS and `git push`
