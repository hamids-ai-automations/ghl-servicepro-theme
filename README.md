# ServicePro — Premium GoHighLevel Website Theme

> Premium, conversion-focused website theme for local service businesses — HVAC, plumbing, roofing, electrical, cleaning and remodeling contractors. One reusable design system, multiple industry demos, lead-generation layouts, and GHL integration guides.

**Repository positioning:** Premium GoHighLevel website theme for local service businesses, featuring reusable components, conversion-focused landing pages, lead-generation forms, responsive layouts and GHL implementation documentation.

---

## Table of contents

1. [Introduction](#introduction)
2. [Live demo](#live-demo)
3. [Features](#features)
4. [Supported industries](#supported-industries)
5. [Technology stack](#technology-stack)
6. [Architecture overview](#architecture-overview)
7. [Project structure](#project-structure)
8. [Installation](#installation)
9. [Configuration](#configuration)
10. [GHL implementation guide](#ghl-implementation-guide)
11. [Customization guide](#customization-guide)
12. [GHL integrations](#ghl-integrations)
13. [SEO implementation](#seo-implementation)
14. [Performance](#performance)
15. [Testing](#testing)
16. [Deployment](#deployment)
17. [Roadmap](#roadmap)
18. [Contributing](#contributing)
19. [License](#license)
20. [Developer](#developer)
21. [Hire Muhammad Hamid](#hire-muhammad-hamid)

---

## Introduction

**ServicePro** is a premium, conversion-focused GoHighLevel website theme built for local service businesses. Rather than publishing a single static template, ServicePro is engineered as a **reusable design system** — one architecture that spins up polished, high-converting websites for any local service industry.

The repository includes **three complete industry demonstrations** (HVAC, Plumbing, Roofing) that share the same components, layout patterns and conversion structure, each re-themed instantly with its own brand palette, copy, services, testimonials, pricing and FAQ.

This project serves two purposes:

1. **A ready-to-customize starting point** for agencies and freelancers building GoHighLevel websites for service businesses.
2. **A portfolio asset** demonstrating Muhammad Hamid's GHL development, conversion design and marketing automation capabilities.

### Value proposition

- **One design system, many industries** — add a new industry by editing a single data file.
- **Conversion-focused** — every section is designed to generate qualified leads.
- **Production-grade** — semantic HTML, accessibility, SEO metadata, responsive layouts.
- **GHL-ready** — documented integration points for forms, CRM, calendars, pipelines and workflows.
- **Honest** — demo content is clearly labeled as fictional samples; no fake ratings in structured data.

---

## Live demo

A hosted preview of the ServicePro theme is available. Use the industry switcher in the header to toggle between HVAC, Plumbing and Roofing demos live.

> **Note:** This repository contains the external Next.js preview of the design system. The live GoHighLevel implementation is delivered as native GHL elements (custom HTML/CSS sections, GHL forms, calendars, pipelines and workflows) via the documented implementation process in [docs/GHL-IMPLEMENTATION.md](docs/GHL-IMPLEMENTATION.md).

---

## Features

### Conversion optimization

- Strong homepage headline with clear value proposition
- Prominent phone and contact CTAs in the sticky header
- Free quote request form with validation and success/error states
- Booking and consultation CTAs throughout the page
- Trust-building testimonials (clearly labeled as demo content)
- "Why choose us" section with credibility points
- Before-and-after project showcase gallery
- Service coverage area pages
- FAQ accordion addressing common objections
- Emergency service CTA banner
- Repeated conversion opportunities across every section
- Sticky mobile CTA bar (Call + Free quote) — always one tap away
- Floating WhatsApp hiring button with pre-filled inquiry messages

### Reusable design system

- Centralized design tokens (colors, fonts, spacing, radius, shadows) via CSS custom properties
- Shared components: header, navigation, footer, hero, service cards, testimonial cards, CTA banners, contact forms, booking sections, pricing cards, FAQ accordions, image galleries, trust badges, service area sections
- Industry-specific color palettes and typography
- Mobile-first responsive layouts with safe-area insets
- Easy customization of business name, logo, brand colors, contact details, hours, service areas, services, images, testimonials and CTA labels — all from a single config file

### Industry demonstrations

Three polished variations using the same design system:

1. **HVAC ServicePro** — Summit Air Heating & Cooling
2. **Plumbing ServicePro** — ClearFlow Plumbing & Drains
3. **Roofing ServicePro** — Summit Peak Roofing & Exteriors

Each variation has industry-specific homepage content, a unique brand palette, appropriate imagery, industry-specific services, relevant conversion CTAs, industry-specific FAQs and relevant forms.

---

## Supported industries

The theme is designed for (and easily extensible to):

- HVAC companies
- Plumbing businesses
- Roofing contractors
- Electrical contractors
- Cleaning companies
- Landscaping businesses
- Painting companies
- Home remodeling companies
- General contractors
- Local maintenance services

---

## Technology stack

| Layer | Technology |
| --- | --- |
| Framework | Next.js 16 (App Router) |
| Language | TypeScript 5 |
| Styling | Tailwind CSS 4 |
| UI components | shadcn/ui (New York style) + Lucide icons |
| State management | Zustand (industry switching) |
| Forms | React Hook Form + Zod validation |
| Animations | Framer Motion |
| ORM | Prisma (SQLite client) |
| Fonts | Geist Sans / Geist Mono |

---

## Architecture overview

ServicePro follows a **data-driven, single-source-of-truth** architecture:

```
Industry Data (src/lib/industries.ts)
        │
        ▼
  Zustand Store (use-industry.ts) ──► active industry
        │
        ▼
  ThemeProvider ──► applies brand palette as CSS custom properties
        │
        ▼
  Reusable Components ──► read from store, render industry-specific content
```

**Key principle:** Adding a new industry requires only a new entry in `src/lib/industries.ts`. No component rewrites. The entire site re-themes instantly because every component reads from CSS custom properties (`--brand`, `--brand-soft`, etc.) set by the `ThemeProvider`.

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for the full architecture breakdown.

---

## Project structure

```
ghl-servicepro-theme/
├── .github/
│   └── workflows/
│       └── ci.yml                  # Lint + type-check on push & PR
├── docs/
│   ├── ARCHITECTURE.md
│   ├── CUSTOMIZATION.md
│   ├── DEPLOYMENT.md
│   ├── GHL-IMPLEMENTATION.md
│   ├── INTEGRATIONS.md
│   ├── INSTALLATION.md
│   └── SEO-GUIDE.md
├── prisma/
│   └── schema.prisma               # Database schema (SQLite)
├── public/
│   ├── images/                     # Hero images (regenerate — see INSTALLATION.md)
│   └── robots.txt
├── src/
│   ├── app/
│   │   ├── api/quote/route.ts      # Lead-capture endpoint
│   │   ├── globals.css             # Design tokens + global styles
│   │   ├── layout.tsx              # SEO metadata + JSON-LD
│   │   ├── page.tsx                # Assembles all sections
│   │   └── sitemap.ts              # Dynamic sitemap
│   ├── components/
│   │   ├── site/                   # ServicePro custom components
│   │   │   ├── about.tsx
│   │   │   ├── contact.tsx
│   │   │   ├── developer-section.tsx
│   │   │   ├── emergency-cta.tsx
│   │   │   ├── faq.tsx
│   │   │   ├── floating-whatsapp.tsx
│   │   │   ├── hero.tsx
│   │   │   ├── icon.tsx
│   │   │   ├── industry-switcher.tsx
│   │   │   ├── legal.tsx
│   │   │   ├── pricing.tsx
│   │   │   ├── process.tsx
│   │   │   ├── projects.tsx
│   │   │   ├── quote-form.tsx
│   │   │   ├── section.tsx
│   │   │   ├── service-areas.tsx
│   │   │   ├── services.tsx
│   │   │   ├── site-footer.tsx
│   │   │   ├── site-header.tsx
│   │   │   ├── sticky-mobile-cta.tsx
│   │   │   ├── testimonials.tsx
│   │   │   ├── theme-provider.tsx
│   │   │   ├── theme-system.tsx
│   │   │   ├── trust-bar.tsx
│   │   │   ├── use-industry.ts
│   │   │   └── why-choose-us.tsx
│   │   └── ui/                     # shadcn/ui components
│   ├── hooks/
│   │   ├── use-mobile.ts
│   │   └── use-toast.ts
│   └── lib/
│       ├── db.ts                   # Prisma client
│       ├── industries.ts           # ← Industry data (single source of truth)
│       ├── site-config.ts          # ← Global site + developer config
│       └── utils.ts
├── .env.example
├── .gitignore
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── README.md
├── components.json                 # shadcn/ui config
├── eslint.config.mjs
├── next.config.ts
├── package.json
├── postcss.config.mjs
├── tailwind.config.ts
└── tsconfig.json
```

---

## Installation

See [docs/INSTALLATION.md](docs/INSTALLATION.md) for the complete step-by-step guide.

**Quick start:**

```bash
git clone https://github.com/hamids-ai-automations/ghl-servicepro-theme.git
cd ghl-servicepro-theme
bun install
cp .env.example .env
bun run db:push
bun run dev
```

Open `http://localhost:3000`.

### Hero images

The three industry hero images are AI-generated and are **not committed** to this repository (binary assets). The theme includes a graceful branded-gradient fallback when images are absent. To generate the hero images, see the [Image generation](docs/INSTALLATION.md#hero-images) section of the installation guide.

---

## Configuration

All business-specific content is centralized in two files — no hardcoded values scattered across components:

| File | Controls |
| --- | --- |
| `src/lib/site-config.ts` | Site name, tagline, nav links, legal links, developer branding, WhatsApp contact |
| `src/lib/industries.ts` | Per-industry: business name, brand palette, hero copy, services, why-us, process, about, testimonials, projects, pricing, service areas, FAQ, contact details, emergency CTA |

See [docs/CUSTOMIZATION.md](docs/CUSTOMIZATION.md) for the full customization guide.

---

## GHL implementation guide

This repository is the **external Next.js preview** of the design system. In production, the theme is implemented in GoHighLevel as native GHL elements.

See [docs/GHL-IMPLEMENTATION.md](docs/GHL-IMPLEMENTATION.md) for the complete implementation method, including:

- How to rebuild sections as GHL custom HTML/CSS sections
- Mapping the quote form to GHL forms, contacts, opportunities and workflows
- Calendar booking integration
- Snapshot export/import where supported
- Honest limitations of native GHL import

---

## Customization guide

See [docs/CUSTOMIZATION.md](docs/CUSTOMIZATION.md).

---

## GHL integrations

See [docs/INTEGRATIONS.md](docs/INTEGRATIONS.md) for documented integration points:

- GHL forms → contact creation
- Opportunity pipelines
- Appointment calendars
- Workflow automation (SMS/email follow-ups)
- Lead source tracking
- Payment links
- Third-party integrations

---

## SEO implementation

See [docs/SEO-GUIDE.md](docs/SEO-GUIDE.md). Technical SEO includes:

- Semantic HTML5 with proper heading hierarchy
- Unique page titles and meta descriptions
- Canonical URLs
- XML sitemap (`/sitemap.xml`)
- `robots.txt`
- Open Graph and Twitter Card metadata
- JSON-LD structured data (WebSite + BreadcrumbList)
- Descriptive image alt text
- Mobile-friendly layouts
- Clean URL structures and internal linking

**Honesty note:** No fake business addresses, ratings, testimonials or reviews are included in structured data. Demo content is clearly labeled as fictional samples throughout the UI.

---

## Performance

- Server-rendered Next.js App Router for fast first paint
- CSS custom properties for instant re-theming (no style recalculation cascades)
- Lazy-loaded images with graceful fallbacks
- Minimal client-side JavaScript (Zustand store is tiny)
- Responsive images with `aspect-ratio` to prevent layout shift

Run Lighthouse against your deployment to measure actual scores. This README does not invent performance numbers.

---

## Testing

```bash
bun run lint      # ESLint (Next.js + TypeScript rules)
```

The CI workflow (`.github/workflows/ci.yml`) runs lint on every push and pull request.

Manual checks to perform before deployment:

- Responsive layout checks (mobile, tablet, desktop)
- Accessibility checks (keyboard navigation, screen reader)
- SEO metadata validation
- Sitemap validation (`/sitemap.xml`)
- Form validation and submission
- Link checks
- Browser compatibility

---

## Deployment

See [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md) for deployment options including Vercel, Netlify, Firebase Hosting and self-hosted.

---

## Roadmap

ServicePro is the flagship theme in a planned portfolio of connected GHL themes:

| Priority | Project | Target clients |
| --- | --- | --- |
| 1 | **ServicePro** ✅ | Contractors and home services |
| 2 | MedSpa Luxe | MedSpa agencies and clinics |
| 3 | EstateFlow | Real estate agencies |
| 4 | AgencyScale | Marketing agencies |
| 5 | DentalCare Pro | Dental practices |
| 6 | LegalLead | Law firms |

Each future theme reuses the ServicePro design-system architecture and links back to this repository and the [Marvis portfolio](https://marvis.web.app/), creating a connected portfolio.

---

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Contributions are welcome — especially new industry demos for the ServicePro theme.

---

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE).

---

## Developer

**Muhammad Hamid**

GoHighLevel Website Developer | GHL Funnel Developer | CRM & Marketing Automation Engineer | AI Automation Developer

- **GitHub:** [hamids-ai-automations](https://github.com/hamids-ai-automations/)
- **Portfolio:** [marvis.web.app](https://marvis.web.app/)
- **WhatsApp:** [+92 316 7417135](https://wa.me/923167417135)

---

## Hire Muhammad Hamid

Need a professional GoHighLevel website, high-converting landing page, custom funnel or complete GHL automation system?

I can help you design, develop and customize a GoHighLevel solution for your business.

[![Hire Muhammad Hamid](https://img.shields.io/badge/WhatsApp-Hire%20Muhammad%20Hamid-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/923167417135)

**Contact Muhammad Hamid on WhatsApp to discuss your project.**

Additional services:

- Request Custom GHL Development
- Build My GoHighLevel Website
- Get a Custom GHL Funnel
- Discuss Your Automation Project
- Request a Website Customization

---

*ServicePro is a portfolio and demonstration project. Demo business names, addresses, phone numbers, reviews and project examples are fictional samples created solely to demonstrate the theme's layout and conversion features.*
