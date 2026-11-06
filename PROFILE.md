# Nexa Essentials — Price & Volume History Cockpit

A single-file, self-contained analytics cockpit covering every SKU a consumer-goods (essentials) business unit has sold since inception — 1,000+ SKUs across ~57 months — with realised price, volume, MoM change, declared DP/TP/MRP grid, price-direction breadth and own-price elasticity.

## The problem it solves
An FMCG/essentials portfolio sells thousands of pack SKUs (rice, lentils, oil, flour, spices, snacks, beverages). Pricing drifts per SKU, some lines grow and others stall, and there was no way to answer "is price rising or falling across the book?", "how elastic is each SKU?" or "what changed when?" without a heavy BI stack.

## The solution approach
One portable HTML file that embeds the whole dataset as a JS object and hand-renders all charts in SVG — no libraries, no server. Tabs let an analyst go from portfolio-level revenue/breadth down to a single SKU's month-on-month journey and elasticity read-out.

## Key features
- Overview: monthly net revenue bars, active-SKU count line, and price-direction breadth (share of SKUs up vs down vs flat).
- All-SKUs: sortable/searchable table of 1,000+ SKUs with revenue, volume, first/last price and MoM change.
- SKU month-on-month: picker + dual-axis price/volume chart + drill table.
- Price change tracker: realised moves and declared-price change events.
- Declared price grid: distributor (DP), trade (TP) and MRP per SKU with realised-vs-declared gap.
- Own-price elasticity computed from log-log OLS per SKU with coverage flags.
- Method & coverage notes documenting the clean window and data caveats.

## Tech stack
- Vanilla JavaScript, zero dependencies; hand-authored SVG charts; CSS grid layout and theming.
- Full dataset embedded as a single `const D = {...}` JSON object (monthly portfolio, per-SKU series, declared prices and change events).

## Demo data
All figures are synthetic placeholders. Revenue, volume, prices and change values were randomized from the original patterns while preserving data structures, SKU counts and order of magnitude so every chart, table and KPI still renders. The company, brand and ERP identifiers are fictional.

## How to run locally
- Open `index.html` directly in a browser, **or**
- Serve statically, e.g. `npx serve .` then visit the printed URL.

## Deploying to Vercel
1. Push this folder to a Git repo.
2. In Vercel, **Import repo** → framework preset: **Other**.
3. Build command: leave blank; Output directory: leave as root (or `public`).
4. Deploy — the static `index.html` is served as-is.
