# ContextQA Design System

**ContextQA** is an AI-powered test automation platform for web, API and mobile QA. It turns recorded user journeys into self-healing end-to-end tests, executes them across browsers and devices, and reports failures with AI-generated root-cause analysis, visual-regression diffs, and Jira handoff — in one workspace.

The product surface includes:

- **Dashboard** — aggregate test posture across Web / API / Mobile (counts, trend chart, success rate, test distribution, consistently-failing cases)
- **Test Case Manager** — table of test cases with status, priority, last-run, environment tags
- **Live Execution** — real-time step-by-step view with captured DOM/screenshot + running timer
- **Run Results / Post-Execution** — full step timeline, AI Failure Analysis, AI Quick-Fix Suggestions, Visual-regression, Video/Trace/Screenshots
- **Test Case Detail / Step Editor** — authoring surface with pre-requisites, step groups, step types (API, AI Agent, Condition, Loop, Verify, etc.)
- **Organization Settings / Environments / Activity Log**

## Sources used to build this system

| Source | Where |
|---|---|
| Figma: "ContextQA Design System V1" | attached (mounted VFS) |
| Figma: "Test Case Details" | attached (mounted VFS) |
| Figma: "Front End Updates (Approved dashboard, Table components, Run results and Live execution)" | attached (mounted VFS) — primary reference for finalized screens |

> Figma files were mounted as pseudocode; design tokens (colors, radii, shadows, type) were read directly from the .jsx. Screenshots used only for layout orientation.

## Brand identity at a glance

- **Name:** ContextQA (a placeholder brand "Hyniva" appears in dashboard mockups — we use **ContextQA** everywhere because it is the canonical product name per URLs like `app.contextqa.com`).
- **Primary color:** Indigo `#3F43EE` (sidebar, primary buttons, links, accents).
- **Supporting platform accents:** green `#00A63E` (API / success), purple `#A855F7` (mobile / AI).
- **Typefaces:** **Inter** for everything — UI, body, metrics, IDs, selectors. **Nunito Sans** is reserved for the brand wordmark and client/workspace names. Two families, no mono.
- **Vibe:** clean, information-dense, trustworthy, modern SaaS — closer to Linear / Vercel than GitHub / Jira. AI features are visually tagged with a purple accent and sparkle glyphs.

## Content fundamentals

Copy is **direct, product-first, lowercase-sentence-case**. Headings use sentence case ("Failure analysis", not "Failure Analysis" — though mixed casing appears). Labels are short and noun-led.

**Voice:** neutral-professional, second-person where the user acts ("Run your tests", "Create test case"), third-person where the system reports ("Backend service returned 500", "2 attempts before failure"). No marketing fluff.

**Patterns observed in figma:**
- Metrics are **big numbers + tiny label** ("Total Test Cases" over "3,847")
- Trends are numeric deltas with sign + color ("+9%" green / "+2%" red)
- Status pills are single-word, capitalized: `Failed`, `Passed`, `Running`, `Aborted`, `Production`, `Staging`
- AI-generated content is always prefixed with a `✦ AI Generated` badge or the sparkle glyph
- Error / root-cause explanations are full sentences, plain English, no stack traces — e.g. "Backend service returned 500 Internal Server Error. This is likely a transient backend issue or data validation failure, not a test problem."
- **Emoji:** not used. Iconography fills that role.
- **First-person / "we":** not used. Product speaks as the system.

## Visual foundations

### Color
Indigo-dominant palette with slate neutrals and a tight semantic set. Large surfaces are white (`#FFFFFF`) on `#F8FAFC` canvas; sidebar is solid `#3F43EE`. Status tints use the 50/100 variants (e.g. `#FEE2E2` for failed pill bg) with 600/700 ink for readability.

### Type
- **Sizes in play:** 10, 11, 12, 13, 14, 16, 18, 20, 22, 24, 30 px
- **Inter** Regular 12/14 for body; Medium for emphasis; Semibold for card titles; 22–30 for big metrics. Tabular numerals (`font-feature-settings: 'tnum'`) on every numeric field.
- **Nunito Sans** ExtraBold 800 at 22 px is the topbar/workspace identity standard. Bold 700 at 32 px is the marketing/wordmark size.
- Letter-spacing tightens on large text (-0.3px)

### Spacing
8-pt baseline grid with 4-pt half-step. Standard card padding: 16–24px. Table row height 40–48px. Sidebar width 280px (collapsed ~64px).

### Cards & containers
- Corner radius: **10–12px** is the system default; pills are 9999; inputs 8px; large feature cards 14–20px.
- Border: 1px solid `#E5E7EB` — visible but never heavy.
- Elevation is subtle — `0 1px 3px rgba(0,0,0,0.1)` for resting cards, `0 10px 15px -3px rgba(0,0,0,0.1)` for floating.
- Sidebar has a directional shadow `2px 0 12px rgba(0,0,0,0.1)`.

### Backgrounds & imagery
- No gradients on primary surfaces. One exception: the **Test Success Rate** meter uses an orange→green progress gradient.
- No hand-drawn illustrations, no textures, no patterns. Occasional soft indigo-tinted full-width section (`#EEF0FF` / `#D8D9FC`).
- Real product screenshots (browser, phone mock) are captured inside dark-chrome frames with traffic-light dots.

### Animation
- No showy animation in the static design. Expect subtle fade/slide transitions (150–200ms, ease-out) on panels and modals, and a running progress bar on live execution.

### Hover / press states
- Buttons: hover lightens brand by ~6% (`#3F43EE` → `#5256F0`). Press darkens (`#3C3FD5`).
- Nav items: active state gets `#8A8CF4` fill on the indigo sidebar; hover is `rgba(255,255,255,0.05)` overlay.
- Cards / rows: hover → light gray background `#F3F4F6`; no elevation change.

### Borders
1px solid. Light gray (`#E5E7EB`) on white surfaces. Focus rings use `#3F43EE` at 40% alpha (2px outer + 1px inner).

### Transparency / blur
Used sparingly — only on the sidebar (overlays use 5–10% white on the indigo) and status-pill hover states. No glassmorphism.

### Iconography
**Material Symbols Outlined** (stroke weight 400, 20–24px) — the figma externals are 100% Material icons (`IconsPlayArrow`, `IconsChevronRight`, `IconsFileUpload`, etc). We substitute with Material Symbols from CDN.

## Iconography

The attached Figma uses the **Material Symbols Outlined** set almost exclusively. We load it from Google Fonts:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@24,400,0,0" />
```

Usage: `<span class="material-symbols-outlined">play_arrow</span>`.

The only custom icon is the **ContextQA logo mark** — a small abstract shape composed in figma (copied to `assets/logo-mark.svg`). The sidebar renders it next to the wordmark.

- **Emoji:** never used in product UI.
- **Unicode glyphs as icons:** never. (Arrows are Material `chevron_right` / `arrow_forward_ios`.)
- **Brand identity icons:** Jira (brand SVG), Font Awesome Brands for integrations. Copied inline where needed.

## Index (what's in this folder)

| Path | Purpose |
|---|---|
| `colors_and_type.css` | All design tokens — color, type, spacing, radii, shadows. Import first in every file. |
| `SKILL.md` | Agent-Skill-compatible entrypoint. Read this to operate the design system. |
| `assets/` | Logos, sample dashboard PNGs, illustration dots |
| `preview/` | The cards shown in the Design System tab (swatches, specimens, component demos) |
| `ui_kits/contextqa-webapp/` | Pixel-accurate HTML+JSX recreation of the ContextQA web app — sidebar, dashboard, run results, live execution |

## Caveats

- Figma shows the dashboard using the brand name **"Hyniva"** — we assume this is a placeholder; all UI kit files use **ContextQA**.
- No static logo image was found in the figma — only a composed vector. We rebuild the ContextQA wordmark with Inter Medium and reuse the sidebar's composed mark for an inline SVG logo.
- **Geist / Geist Mono / SF Pro Text** appear in older Figma frames. Ignored — only Inter and Nunito Sans are canonical.
- Fonts are loaded via Google Fonts CDN. If you need self-hosted TTF/WOFF, flag it and we'll embed.
