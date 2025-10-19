---
ssot_type: APP_IDEA
id: app-reskin-studio
version: 0.2.0
status: draft
owner: "moez salhi"
created_at: 2025-10-18
last_updated: 2025-10-18
current_phase: initialization
tags: [ux, ui, modernization, web-upgrade, automation, ai-assisted, nextjs, tailwind, lighthouse, a11y, seo, ttv]
---

# 0. Executive Snapshot (Context Rescue)
**Goal:**  
Provide an AI-assisted platform that upgrades outdated websites to modern UX/UI automatically.  
Customers supply their existing website URL and minimal brand info; the system crawls, analyzes, and proposes **3–5 high-level UX/UI themes**.  
Once the client chooses a theme, the platform re-skins their entire site—preserving content, SEO, and accessibility—into a clean, modern codebase.

**Vision:**  
Empower small and mid-size businesses to modernize their digital presence in days, not months, without costly redesigns.

**Users:**  
- Business owners with legacy sites.  
- Freelancers/agencies wanting automated re-skins.  
- Internal digital teams maintaining multiple brand sites.

**Success Metrics:**  
- Time to first theme preview ≤ 24 h.  
- Time to MVP upgraded site ≤ 5 days.  
- Lighthouse: Performance ≥ 85, Accessibility ≥ 95, SEO ≥ 90.  
- Automation coverage ≥ 80% for brochure/content sites.

---

# 1. Initial Requirement (Single Source of Truth)
**Input:**  
- Website URL  
- Optional: brand colors, logo, preferred font, business type, target tone.

**Process Overview:**  
1. Crawl + analyze site structure, layout, palette, and typography.  
2. Identify reusable content blocks and navigation hierarchy.  
3. Present multiple design themes with live previews.  
4. Apply selected theme → regenerate codebase with modern stack (Next.js + Tailwind + shadcn/ui).  
5. Validate a11y, SEO, performance; deploy preview.

**Scope (In):**  
- Static & semi-dynamic sites (marketing, blog, portfolio, small business).  
- Structure detection, design token extraction, automated theme mapping.  
- Code output as static HTML/CSS or Next.js bundle.  
- A11y and SEO remediation.

**Scope (Out / Future):**  
- Complex e-commerce, booking, or app-logic migrations (Phase 2+).  
- Multi-language handling (Phase 2).  
- CMS admin dashboards or user auth (Phase 3).

**Constraints:**  
- Must preserve URL structure (or output redirect map).  
- Maintain SEO meta data and content hierarchy.  
- Respect robots.txt and copyright boundaries.

**Acceptance v0:**  
✅ 3 design themes generated.  
✅ 5 key pages re-skinned with component mapping.  
✅ Lighthouse > 85 Perf / 95 A11y.  
✅ Visual diff ≤ 2 % deviation vs. preview.

---

# 2. Benchmark & Reuse First
| Candidate | Type | License | Maturity | Fit | Notes |
|------------|------|----------|-----------|------|-------|
| Next.js | framework | MIT | High | 5 | modern SSR/SSG base |
| Tailwind CSS | utility framework | MIT | High | 5 | design tokens + speed |
| shadcn/ui | component library | MIT | High | 5 | consistent accessible UI |
| Playwright | crawler | Apache 2.0 | High | 5 | headless capture |
| axe-core | a11y checker | MPL 2.0 | High | 5 | automated fixes |
| Lighthouse CI | audit | Apache 2.0 | High | 5 | perf/SEO baseline |
| OpenAI GPT-5 | AI reasoning | commercial | High | 5 | theme reasoning + mapping |
| sharp | image optimizer | Apache 2.0 | High | 4 | responsive media |

**Decision:**  
Reuse proven frameworks; orchestrate AI for mapping + code synthesis; enforce measurable QA gates.

---

# 3. Solution Direction (Provisional)
**Architecture:**  
[Crawler] → [Analyzer] → [Theme Selector] → [Transformer] → [QA & Export]

**Pipeline steps:**
1. Crawl & extract HTML → site_map.json + blocks.json  
2. Analyze: typography, color palette, layout patterns  
3. Suggest themes (based on site type + brand palette)  
4. Transform: apply tokens + new components  
5. QA: run axe/Lighthouse + visual diff  
6. Output: Next.js/Tailwind bundle or static export  

**Automation coverage:**  
- Prototype: 85–90 %  
- POC: 80–85 %  
- Full site: 65–80 % (manual widgets flagged)

**Risks:**  
- Legacy scripts/widgets.  
- Inline styles / table layouts.  
- Missing meta data.  
**Mitigation:** isolate unsupported blocks; fallback wrappers; human-in-loop review.

---

# 4. Phase Plan (Time-to-Value)
| Phase | Objective | Deliverable | Duration |
|-------|------------|--------------|-----------|
| Prototype | Crawl + 1 theme render | static 2-page demo | 2 days |
| POC | 3 themes + 5 pages | live theme picker + QA | 5 days |
| MVP | 5 themes + full sitemap | deployable bundle | 10–14 days |
| Phase 2 | CMS export + widgets | WP/Webflow theme, multi-lang | +5 days |

---

# 5. AI Automation Scope
| Area | Automation Level | Method |
|------|-------------------|--------|
| Crawl & extraction | 100 % | Playwright scripts |
| Palette & font detection | 100 % | DOM + CSS parser |
| Theme recommendation | 90 % | LLM heuristic |
| Component mapping | 85 % | LLM + few-shot training |
| Copy refinement | 80 % | LLM grammar + tone rule |
| Code generation | 80 % | Template synthesis |
| QA (a11y/perf/SEO) | 95 % | axe + Lighthouse |
| Final review | 20 % human | manual approval |

---

# 6. Deliverables & Acceptance
**Deliverables**
- `site_map.json`, `component_map.json`, `tokens.json`  
- 3–5 theme previews (screens + live URL)  
- Transformed code (Next.js + Tailwind)  
- `qa_report.md` (a11y/perf/SEO metrics)  
- Optional CMS export (WordPress/Webflow)

**Acceptance**
- Pages parity verified; SEO meta preserved.  
- Lighthouse ≥ 85 / 95 / 90.  
- 0 critical axe issues.  
- Visual diff ≤ 2 %.  
- Deployable bundle on Vercel/Netlify.

---

# 7. Decision Log
- **2025-10-18** – Defined *ReSkin Studio* concept.  
- **2025-10-18** – Adopted Next.js + Tailwind + shadcn/ui.  
- **2025-10-18** – Planned AI-assisted component mapping pipeline.

---

# 8. Change Log
- v0.1.0 – Initial draft.  
- v0.2.0 – Added automation matrix + measurable QA gates.

---

# 9. Glossary
**LLM** – Large Language Model (AI reasoning agent).  
**Tokens** – Color/spacing/typography design variables.  
**Component map** – JSON linking old HTML selectors to new UI components.  
**Re-skin** – Replace styles & components while preserving content.  
**A11y** – Accessibility (WCAG 2.1 AA).  
**TTV** – Time-to-Value (speed from idea → usable site).  

