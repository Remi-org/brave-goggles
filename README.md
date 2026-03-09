<p align="center">
  <img src=".github/logo.svg" alt="Remi" width="120">
</p>

<h1 align="center">Brave Search Goggles</h1>

<p align="center">
  Custom <a href="https://search.brave.com/goggles">Brave Goggles</a> that boost authoritative domains by category.<br>
  Used by <a href="https://remiapp.ai">Remi</a> to improve web search quality.
</p>

---

## Categories

| Goggle | Domains | Coverage |
|--------|---------|----------|
| **health** | 126 | WHO, NIH, NHS, medical journals, hospitals |
| **travel_transit** | 107 | Rail operators, transit agencies, travel guides |
| **news** | 140 | Wire services, broadcasters, broadsheets |
| **tech_docs** | 202 | Language docs, frameworks, cloud providers |
| **government_legal** | 147 | Government portals, courts, legislation |
| **finance_business** | 117 | Central banks, exchanges, business news |
| **shopping_prices** | 80 | Consumer testing, price comparison, reviews |
| **food_cooking** | 100 | Recipe platforms, food magazines, nutrition |
| **sports_fitness** | 130 | Governing bodies, sports news, fitness |
| **education_learning** | 78 | MOOCs, universities, academic databases |
| **entertainment_culture** | 117 | Film, music, gaming, arts, museums |
| **home_diy** | 91 | Home improvement, gardening, interior design |
| **weather** | 53 | Met services, climate science, forecasts |

## How It Works

Goggles re-rank Brave Search results without removing anything. Each `.goggle` file contains boost rules organized into five tiers:

| Tier | Boost | Meaning |
|------|-------|---------|
| 5 | `$boost=5` | Gold standard sources (WHO, Reuters, MDN) |
| 4 | `$boost=4` | Major trusted sources |
| 3 | `$boost=3` | Specialized and regional |
| 2 | `$boost=2` | Supplementary |
| 1 | `$boost=1` | Niche |

Some goggles also downrank known low-quality sources using `$downrank`.

## Usage

Register a goggle at [search.brave.com/goggles/create](https://search.brave.com/goggles/create) using the raw GitHub URL, then pass it as `goggles_id` in the Brave Search API:

```
GET https://api.search.brave.com/res/v1/web/search?q=symptoms+of+flu&goggles_id=https://raw.githubusercontent.com/Remi-org/brave-goggles/main/health.goggle
```

## Design Principles

- **Boost only** &mdash; never `$discard`, results are re-ranked not removed
- **Global** &mdash; domains from US, UK, Europe, Asia, Africa, Latin America
- **Tiered** &mdash; authority levels from tier 5 (highest) to tier 1

---

<p align="center">
  <a href="https://remiapp.ai">remiapp.ai</a>
</p>
