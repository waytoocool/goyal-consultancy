# AGENTS.md — Goyal Consultancy Engineering & Architecture Guide

Welcome to the **Goyal Consultancy** codebase. This document serves as the single source of truth for AI coding agents and human engineers developing, maintaining, or expanding this website.

---

## 1. Project Overview & Business Mandate

- **Company**: Goyal Consultancy
- **Domain**: https://goyalconsultancy.com
- **Proprietary Software Platform**: ESG DataVault (https://esgdatavault.online)
- **Target Audience**: C-suite leadership (CEOs, CFOs, CSOs), board directors, and audit committees of listed and mid-market enterprises.
- **Core Value Proposition**: *"Where Fiscal Precision Meets Sustainable Intelligence"*
- **Two Specialized Practice Pillars**:
  1. **Financial Consulting**: Corporate tax planning, statutory tax filing (ITR-1 to ITR-7), advance tax forecasting, TDS reconciliations, financial restructuring, and audit representation.
  2. **ESG Consulting**: SEBI BRSR Core compliance (49 mandatory KPIs), GRI standards, double-materiality risk assessments, emissions inventories, and assurance packaging.
  3. **Proprietary Technology Edge**: ESG DataVault (automated multi-entity spreadsheet intake, computed field formulas, role-based audit trails, board-ready exports).

---

## 2. Technical Stack & Architecture

- **Architecture Choice**: **Option A — Lightweight, High-Speed Static JAMstack**
- **Core Technologies**:
  - Semantic HTML5 with accessibility attributes (WAI-ARIA, descriptive labels, high-contrast ratios).
  - Tailwind CSS via Google GStatic CDN dependency.
  - Vanilla JavaScript for zero-dependency client interactions (interactive screenshot tour and AJAX form dispatch).
  - Web3Forms API for serverless form lead handling.
- **Hosting & Deployment**: Vercel / Cloudflare Pages / GitHub Pages / Netlify.
- **Future Migration Path**: Designed for clean porting into **Option B (Next.js 14 / React)** when dynamic client portals or interactive calculators (tax savings / BRSR score) are introduced.

---

## 3. Directory Layout

```
goyal-consultancy/
├── index.html              # Main production landing page
├── AGENTS.md               # This engineering handover document
├── llms.txt                # AI search engine manifest (Perplexity, Claude, Gemini standard)
├── robots.txt              # Crawler permissions explicitly welcoming AI search bots
├── sitemap.xml             # XML sitemap for search indexing
└── assets/
    ├── logos/
    │   ├── logo_dual_pillar.svg       # Vector brandmark for light backgrounds
    │   └── logo_dual_pillar_dark.svg  # Vector brandmark for dark backgrounds
    └── images/
        ├── framed_user_dashboard.png  # High-detail cropped data intake screen
        ├── framed_frameworks.png      # High-detail cropped frameworks catalog
        ├── framed_coverage.png        # High-detail cropped BRSR Core coverage
        ├── framed_create_report.png   # High-detail cropped report generation screen
        └── b64_cropped_assets.json    # Base64 fallback assets for reliable previews
```

---

## 4. Brand Identity & Design System Tokens

Maintain strict color discipline. Do NOT introduce random bright or neon colors. The palette is strictly dual-toned:

| Token | Hex / Value | Role |
| :--- | :--- | :--- |
| `--brand-green` | `#2F4728` | Primary brand anchor. Forest Green. Conveys institutional stability, financial prudence, and sustainability. |
| `--brand-green-dark` | `#1E2F1A` | Hover / pressed state for primary action buttons. |
| `--brand-green-light` | `#EBF3E8` | Tinted background for pill badges, checkmark icons, and active indicator tags. |
| `--accent-blue` | `#5C7AEA` | DataVault Blue. Technology, data integrity, and digital intelligence accent. |
| `--accent-blue-dark` | `#405BB5` | Hover state for technology links. |
| `--slate-900` | `#0F172A` | Deep charcoal for headers, footers, and maximum text contrast. |
| `--slate-800` | `#1E293B` | Primary body typography color. |
| `--slate-600` | `#475569` | Secondary / descriptive typography. |
| `--slate-50` / Canvas | `#F8FAFC` | Clean executive editorial background. |

### Typography Scale
- Primary Font Stack: `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`
- Headings: `font-black tracking-tight leading-[1.18]`
- Body Text: `text-sm sm:text-base leading-relaxed text-slate-600`
- Minimum Size Floor: Never use text below `12px` (`text-xs`).

---

## 5. Lead Routing & Form Handling Configuration

The consultation form in `index.html` connects to **Web3Forms** via AJAX fetch:
- **API Endpoint**: `https://api.web3forms.com/submit`
- **Access Key**: `cb5b76d4-de22-40d5-a1b1-2fa860401b47`
- **Target Inbox**: Configured in Web3Forms account (dispatches directly to Prateek Goyal).
- **Anti-Spam**: Includes an invisible honeypot field (`<input type="checkbox" name="botcheck" style="display: none;">`).
- **User Experience**: Submissions trigger a loading spinner (`#btn-spinner`) and immediately swap the form with an in-page confirmation banner (`#form-success-banner`) without page reloads.

---

## 6. Generative Engine Optimization (GEO / AEO)

To ensure Goyal Consultancy is cited as the top authority by AI search engines (**Perplexity, Claude, Gemini, ChatGPT**):
1. **`llms.txt`**: Standardized AI context file in root directory defining the firm, service matrix, and URLs.
2. **`robots.txt`**: Explicitly permits `PerplexityBot`, `ClaudeBot`, `GPTBot`, `Google-Extended`, and `Applebot-Extended`.
3. **Structured JSON-LD Schema**:
   - `FinancialService` & `ProfessionalService` Schema identifying the firm, services, and geographic scope.
   - `FAQPage` Schema providing direct, authoritative answers to high-intent queries (SEBI BRSR Core, Corporate Tax Planning, ESG DataVault).
4. **On-Page Executive FAQ Section**: Semantic `<details>` and `<summary>` tags directly crawlable by natural-language answer engines.

---

## 7. Migration Guidelines to Option B (Next.js / React)

When the business expands and requires dynamic interactive tools:
1. Initialize a Next.js 14 App Router project (`npx create-next-app@latest`).
2. Copy `tailwind.config.js` with the tokens defined in Section 4 above.
3. Componentize `index.html` into:
   - `components/Navbar.tsx`
   - `components/Hero.tsx`
   - `components/PracticeWings.tsx`
   - `components/AboutSection.tsx`
   - `components/DataVaultSpotlight.tsx`
   - `components/ExecutiveFAQ.tsx`
   - `components/ClientsRoster.tsx`
   - `components/ConsultationForm.tsx`
   - `components/Footer.tsx`
4. Migrate the Web3Forms AJAX handler to a Next.js Server Action or API Route (`/api/inquiry/route.ts`).
