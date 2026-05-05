# ☕ Coffee Quality Analysis — Power BI Capstone Project

> An interactive, multi-page Power BI dashboard for deep-dive analysis of Arabica coffee quality metrics across origins, processing methods, defect profiles, and harvest timelines.

---

## Overview

The global specialty coffee industry relies on rigorous quality evaluation systems — yet raw cupping data is rarely visualized in a way that enables fast, actionable insight. This capstone project bridges that gap.

**Coffee Quality Analysis** is a fully interactive Power BI report built on real-world Arabica coffee grading data sourced from the Coffee Quality Institute (CQI). The dashboard enables analysts, agronomists, importers, and coffee buyers to explore how geographic origin, processing method, bean variety, and harvest year influence sensory scores and defect rates — all through a polished, navigable visual interface.

The report answers questions such as:
- Which countries and regions consistently produce the highest-scoring Arabica lots?
- How do processing methods (washed, natural, honey) affect cup quality and defect incidence?
- What sensory attributes — aroma, acidity, body, balance — drive the Total Cup Points score?
- How have defect rates and quality benchmarks trended across harvest years?

---

## Features

- **5-page analytical dashboard** with a dedicated navigation home page, each page focused on a distinct analytical theme
- **8 interactive slicers per page** enabling cross-filtering by country, variety, processing method, harvest year, color, altitude, and more
- **6 KPI summary cards per page** surfacing key metrics at a glance (Total Cup Points, defect counts, moisture %, bag weight, partner count)
- **Scatter plot analysis** correlating moisture percentage against quality scores and defect magnitude
- **Treemap visualizations** for hierarchical breakdowns of variety distribution and processing method groupings
- **Combo charts (line + column)** for multi-metric comparison across categories and time
- **Donut and pie charts** for proportional analysis of processing methods and defect type splits
- **Area charts** for trend visualization across harvest periods
- **Detailed data table** on the Origin Region page for granular lot-level inspection
- **Custom branding** with coffee-themed imagery, "Electric" Power BI theme, and logo integration
- **Page-level navigation** via button shapes linking directly between report sections
- **Clean dataset** of 207 Arabica coffee lots across 31 quality, origin, and physical attributes

---

## Tech Stack

| Category | Technology |
|---|---|
| **BI & Visualization** | Microsoft Power BI Desktop (v1.28, Cloud-created, Release 2025.07) |
| **Data Format** | CSV (cleaned and pre-processed) |
| **Report Theme** | Power BI "Electric" built-in theme |
| **Data Source** | Coffee Quality Institute (CQI) — Arabica cupping records |
| **Asset Format** | PBIX (Power BI report + embedded data model) |
| **Branding Assets** | JPEG (coffee logo, roasted beans background) |

---

## System Architecture / Workflow

```
Raw CQI Arabica Data
        │
        ▼
┌─────────────────────┐
│  Data Cleaning &    │
│  Preprocessing      │  → df_arabica_clean.csv (207 rows × 31 columns)
└─────────────────────┘
        │
        ▼
┌─────────────────────┐
│  Power BI Data      │
│  Model (DataModel)  │  → Embedded in .pbix, relationships auto-resolved
└─────────────────────┘
        │
        ▼
┌───────────────────────────────────────────────────────┐
│                  Report Layout                         │
│                                                       │
│  Page 1: Navigation Hub                               │
│    └─ Button shapes linking to all 5 analysis pages  │
│                                                       │
│  Page 2: Coffee Quality Analysis (Overview)           │
│    └─ Slicers, KPI cards, column/area/scatter/pie    │
│                                                       │
│  Page 3: Processing Methods Analysis                  │
│    └─ Bar, treemap, combo, donut, pie charts         │
│                                                       │
│  Page 4: Origin Region Analysis                       │
│    └─ Data table, bar chart, pie chart               │
│                                                       │
│  Page 5: Defects Analysis                             │
│    └─ Area chart, donut, pie, bubble scatter plot    │
│                                                       │
│  Page 6: Time Series Analysis                         │
│    └─ Line charts, combo charts, column, treemap     │
└───────────────────────────────────────────────────────┘
        │
        ▼
   End User: Interactive exploration via slicers,
   cross-filtering, drill-through, and page navigation
```

**Data flow summary:**

1. **Source data** — CQI Arabica grading records are cleaned and exported as `df_arabica_clean.csv`
2. **Import** — The CSV is loaded into Power BI's internal columnar data model (VertiPaq engine)
3. **Modeling** — Calculated fields and implicit measures (aggregations on cup points, defect counts, bag weights) are defined within the model
4. **Report layer** — Six report pages each host a dedicated set of visuals powered by the same underlying model
5. **Interactivity** — Slicer panels on each page drive cross-visual filtering in real time; navigation shapes provide page routing

---

## Usage

### Navigating the Dashboard

| Page | Purpose |
|---|---|
| **Page 1 — Home** | Navigation hub; click buttons to jump to each analysis section |
| **Page 2 — Coffee Quality Analysis** | Overview of sensory scores, moisture, defects, and key quality drivers |
| **Page 3 — Processing Methods Analysis** | Compare quality metrics across washed, natural, honey, and specialty methods |
| **Page 4 — Origin Region Analysis** | Country- and region-level breakdown of partner distribution and quality |
| **Page 5 — Defects Analysis** | Defect category deep-dive; scatter plots correlating defects vs. quality |
| **Page 6 — Time Series Analysis** | Harvest year trends in cup points, defects, and physical attributes |

### Using Slicers

Each page features **8 slicers** that can be used individually or in combination:
- **Country of Origin** — Filter to one or more producing nations (Taiwan, Guatemala, Colombia, etc.)
- **Processing Method** — Washed / Wet, Natural / Dry, Pulped natural / Honey, and specialty methods
- **Variety** — Gesha, Caturra, Typica, Bourbon, Catuai, Catimor, Ethiopian Heirlooms, etc.
- **Harvest Year** — Ranges from 2021 through 2022/2023
- **Color** — Green, greenish, blue-green, yellowish, brownish, etc.
- **Altitude** — Elevation ranges of growing regions
- Additional slicers vary per page (e.g., defect category, bag weight range)

---

## Dataset Reference

**File:** `df_arabica_clean.csv`
**Records:** 207 Arabica coffee lots
**Columns:** 31

| Column Group | Fields |
|---|---|
| **Identity / Provenance** | ID, Country of Origin, Region, Lot Number, In-Country Partner, Harvest Year, Grading Date, Expiration |
| **Physical Attributes** | Altitude, Number of Bags, Bag Weight, Moisture Percentage, Color |
| **Processing** | Variety, Processing Method, Status |
| **Sensory Scores (0–10)** | Aroma, Flavor, Aftertaste, Acidity, Body, Balance, Uniformity, Clean Cup, Sweetness, Overall |
| **Quality Summary** | Total Cup Points (range: 78.0–89.33, mean: 83.71) |
| **Defects** | Defects, Category One Defects, Category Two Defects, Quakers |

---

## Project Structure

```
Capstone Project/
│
├── Coffee Quality Analysis1.pbix     # Main Power BI report file (data model + all 6 pages)
│
├── df_arabica_clean.csv              # Cleaned Arabica grading dataset (207 lots × 31 attributes)
│
├── coffee logo.jpg                   # Branding asset — coffee brand logo
│
└── roasted-coffee-beans.jpg          # Branding asset — background/hero image
```

> Both JPEG assets are embedded inside the `.pbix` archive at `Report/StaticResources/RegisteredResources/` and are used for visual branding across report pages.

---

## Key Highlights

- **Real-world dataset:** Built on Coffee Quality Institute grading data — the same scoring methodology used by professional Q-graders and specialty coffee importers worldwide
- **Comprehensive sensory coverage:** All 9 SCA cupping protocol attributes (Aroma, Flavor, Aftertaste, Acidity, Body, Balance, Uniformity, Clean Cup, Sweetness) are represented and filterable
- **Defect taxonomy:** Distinguishes between Category One defects (severe, affecting green beans — e.g., full blacks, full sours) and Category Two defects (less severe — e.g., partial blacks, floaters/quakers)
- **Multi-dimensional slicing:** Every analytical page supports 8 simultaneous filters, enabling precise segment isolation without writing any DAX queries
- **Navigation-first UX:** Page 1 functions as a visual menu — an unusual but effective UX pattern for Power BI that significantly reduces report navigation friction
- **Combo chart strategy:** Line + stacked column combo charts are used to overlay two related metrics (e.g., cup points trend vs. defect volume) in a single visual, reducing page clutter
- **Treemap for variety/method distribution:** Treemaps surface proportional breakdowns that pie charts cannot express clearly at >5 categories

---

## Future Improvements

- **Add a geographic map visual** — Plotting producing countries on a filled map with bubble size encoding average cup points would add immediate spatial context
- **DAX measures for score grading bands** — Classify lots into SCA specialty tiers (80–84.99: Very Good, 85–89.99: Excellent, 90+: Outstanding) as calculated columns for richer filtering
- **Correlation matrix visual** — A custom visual or matrix heatmap showing pairwise correlations between all 9 sensory attributes and Total Cup Points
- **Publish to Power BI Service** — Deploy to the Power BI cloud platform to enable shared access, scheduled refresh, and mobile layout
- **Altitude normalization** — The Altitude column contains mixed formats (ranges like "1700-1930" and single values like "1200"). Parsing these into a numeric midpoint would unlock altitude-based analysis
- **Row-level security (RLS)** — For a multi-user deployment, RLS could restrict partner visibility per organizational role
- **Natural language Q&A** — Enable Power BI's Q&A visual so non-technical stakeholders can query the data in plain English
- **Predictive scoring model** — Integrate an Azure Machine Learning model to predict Total Cup Points from physical attributes and origin metadata

---

## Screenshots / Demo

> Screenshots are not included in this repository. To view the live dashboard, open `Coffee Quality Analysis1.pbix` in Power BI Desktop.

**Expected page previews:**

| Page | Key Visual |
|---|---|
| Home | Navigation button grid with coffee branding |
| Coffee Quality Analysis | Scatter plot: Moisture % vs. Cup Points; clustered column chart by acidity |
| Processing Methods Analysis | Treemap of variety × method; donut of processing method share |
| Origin Region Analysis | Bar chart of countries by quality; data table of lot-level records |
| Defects Analysis | Bubble scatter: defect volume × cup points × bag weight |
| Time Series Analysis | Line chart of cup points trend by harvest year |

---

> **Data Source:** Coffee Quality Institute (CQI) — Arabica Green Coffee Grading Database
> **Tool:** Microsoft Power BI Desktop 2025.07
> **Domain:** Specialty Coffee Quality Analytics
