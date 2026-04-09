# Brand Refresh Analysis Dashboard

A single-file, interactive HTML dashboard for evaluating distressed and dormant consumer brands across **Beauty**, **Health**, **Wellness**, and **Personal Care** — identifying the highest-potential candidates for revitalization.

---

## Overview

This tool is designed for internal strategic use. It tracks brands that once commanded meaningful category market share but have since declined, and helps teams triage, compare, and document top acquisition or revival candidates.

The dashboard is entirely self-contained — no backend, no dependencies to install. Open the HTML file in any modern browser and you're up and running.

---

## Features

### Executive Summary Tab
- **Key stats** — total brands evaluated, brands in consideration pool, and recommended brands
- **Brand universe breakdown** by category (Beauty, Health, Wellness, Personal Care)
- **Brand Life Cycle chart** — SVG visualization showing where distressed brands sit on the market relevance curve
- **Editable text blocks** — scope of analysis, selection criteria, exclusion filters, and methodology notes can be edited and saved directly in the browser
- **Recommendation rationale** — editable summary of why top-tier brands are highlighted

### Brand Analysis Tab
- **Three-tier system:**
  - **Recommended for Consideration** — top candidates, displayed in a highlighted table
  - **Brand Overview** — wider consideration pool
  - **Brand List** — full evaluated universe displayed as cards
- **Brand cards** with category color-coding, key metrics (peak sales, current sales, peak share, current share, estimated valuation), and quick-action buttons
- **Search** — real-time search across brand names and descriptions
- **Category filters** — filter by Beauty, Health, Wellness, or Personal Care
- **Sort/attribute filters** — sort by lowest valuation, highest/lowest current sales, largest sales or share drop, and more
- **Promote / Demote** — move brands between tiers with a single click
- **Compare tool** — select multiple brands and view a side-by-side comparison modal
- **Brand detail modal** — full metrics, description, and notes for each brand
- **Edit brand** — update any brand's data fields inline
- **Add new brand** — add brands manually or import via CSV/Excel upload
- **Export to Excel** — export the full brand list or any tier to `.xlsx`
- **Delete brands** — remove brands from the universe with a confirmation prompt

### Persistence
- All tier assignments, edits, and executive summary content are saved to **localStorage** automatically — your work persists across browser sessions without any server

---

## Getting Started

1. Clone or download the repository
2. Open `brand-refresh-dashboard.html` in any modern browser (Chrome, Firefox, Safari, Edge)
3. No installation, build step, or internet connection required

```bash
git clone https://github.com/brodeur904-creator/Distressed-Brands.git
cd Distressed-Brands
open brand-refresh-dashboard.html
```

---

## Selection Criteria

Brands included in the universe meet all of the following:

| Criterion | Threshold |
|---|---|
| Peak U.S. category market share | > 5% at any point after 1970 |
| Current U.S. category market share | < 1% as of 2026 |
| Sales/share decline from peak | ≥ 80% |
| Peak popularity era | Post-1970, indexed toward 1990s–2010s |
| Aided brand awareness | > 40% among U.S. consumers |

**Exception:** DTC lifestyle health brands (e.g., Jenny Craig) are included regardless of OTC market share metrics.

### Exclusions

- Brands with estimated current valuation > $250M (e.g., Revlon)
- Brands whose decline was primarily driven by FDA regulation or OTC compliance failure
- Brands still operating at or near peak levels
- Brands with severe unresolved reputational damage (safety recalls, active litigation)
- Private label or white-label derivatives without standalone brand equity
- Micro-brands lacking sufficient consumer awareness data

---

## Data & Disclaimers

All data reflects publicly available information as of **Q1 2026**. Brand financial metrics are estimated based on available filings, press reports, and industry databases.

> This analysis is intended for **internal strategic discussion only** and does not constitute investment advice.

---

## Tech Stack

- **Vanilla HTML/CSS/JavaScript** — zero frameworks, zero build tools
- **DM Sans** (Google Fonts) for UI typography; **Times New Roman** for editorial headings
- **SheetJS (xlsx.js)** via CDN — used for Excel export functionality
- **localStorage** — client-side persistence for tier assignments and edits

---

## File Structure

```
Distressed-Brands/
└── brand-refresh-dashboard.html   # Entire application in one file
```

---

## Contributing

To add or update brand data, edit the `BRAND_DATA` array in the `<script>` section of `brand-refresh-dashboard.html`. Each brand object supports the following fields:

```js
{
  id: "unique-id",
  name: "Brand Name",
  category: "Beauty" | "Health" | "Wellness" | "Personal Care",
  description: "Short description",
  peakSales: "$500M",
  currSales: "$10M",
  peakShare: "12%",
  currShare: "0.2%",
  valuation: "$25M",
  lastAcqPrice: "$18M",
  notes: "Optional internal notes"
}
```
