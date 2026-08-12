# Andes Retail Group — Commercial Performance & Profitability Dashboard (2024–2025)

An end-to-end analysis of a multi-country retail chain's commercial performance, combining a Python data validation pipeline with an interactive Power BI dashboard, built to identify where revenue is concentrated, why winter sales drop, and where the business should focus its next growth push.

## Business Context

Andes Retail Group is a retail chain operating across **Peru, Chile, and Colombia**, selling across multiple product categories and customer segments (Premium, Standard, Economic). This project evaluates commercial and financial performance over the 2024–2025 period to answer three strategic questions:

- How are revenue and profitability distributed by country, category, and customer segment?
- What seasonal patterns affect sales volume?
- Where are the biggest opportunities for commercial optimization and growth?

## Key Business Findings

- **$5.53M in total revenue, $1.94M in profit, a stable 35.10% margin** — a healthy and consistent baseline across the full 2024–2025 period.
- **Revenue is geographically concentrated**: Peru and Chile account for ~75% of total revenue between them, with Colombia trailing well behind.
- **Segment concentration is even sharper**: Premium and Standard customers drive 92% of sales, leaving the Economic segment at just ~8%.
- **Winter is a volume problem, not a margin problem.** Margin stays remarkably stable year-round (34.85%–35.30% across seasons), but Summer generates 3.43x the revenue of Winter — a ~71% seasonal drop that isn't explained by profitability erosion, only by lower sales volume.
- **Electronics in Peru is the single most profitable combination in the portfolio**, with a 35.38% margin — the natural anchor for a targeted winter campaign.
- **Region (North/Center/South) has no explanatory power over the seasonal drop** — the winter contraction is consistent across regions, ruling out a purely geographic fix.

## Recommendation

Launch a **winter volume-acceleration campaign** targeted at Premium and Standard customers, anchored on the Electronics category in Peru and Chile — the highest-margin combination in the portfolio. Since margin doesn't erode in winter, the opportunity is purely about driving transaction volume during the low season, not defending profitability.

## Methodology

**Data preparation & validation (Python)**
- Explicit type casting: dates to `datetime`, monetary fields to numeric
- Business rule: `Nivel_Venta` (Sale Level) — `"High Sale"` if `Ingresos >= 1000`, else `"Low Sale"`
- Calculated metrics: `Ganancia` (Profit) = `Ingresos - Costo`; `Margen %` = `Ganancia / Ingresos`
- Seasonal ordering map for time-based analysis (Summer: 1, Fall: 2, Winter: 3, Spring: 4)
- Global KPI validation in Python (revenue, profit, margin, order count, unique customers) to cross-check the Power BI data model before publishing

**Dashboard (Power BI)**

Built as a two-level report:

- **Executive Overview** — headline KPIs (revenue, profit, units sold), revenue by country, revenue by customer segment, monthly revenue trend
- **Detail & Profitability View** — combined bar/line chart of revenue and margin % by season, profit trend by customer segment over time, a fully auditable matrix (country × category × order count × unique customers × revenue × profit × margin %) with conditional formatting, and slicers for date, country, region, product category, and customer segment

**Narrative (SCQA framework)**

Both dashboard views are backed by a Situation–Complication–Question–Answer narrative connecting the numbers to a specific, actionable recommendation — included in full in the case study notes.

## Repository Structure

```
├── notebooks/
│   └── andes_retail_data_validation.ipynb
├── data/
│   └── Andes_Retail_Group_2024_2025.csv
├── dashboard/
│   └── andes_retail_group_dashboard.pbix
├── screenshots/
│   ├── 01_executive_overview.png
│   └── 02_profitability_seasonality_detail.png
└── README.md
```

## Tech Stack

Python (pandas, NumPy) · Power BI Desktop · Power Query (M) · DAX

## Limitations

The analysis is descriptive rather than predictive — it explains *what* happened across countries, segments, and seasons, but doesn't forecast future demand. Region (North/Center/South) was tested as a possible driver of the seasonal drop and ruled out, but other unmeasured factors (local competition, macroeconomic conditions per country) aren't captured in this dataset.

## Next Steps

- Design and A/B test a winter volume campaign for Premium and Standard customers before committing full marketing budget
- Investigate why the Economic segment stays flat year-round — is it a pricing issue, an awareness issue, or simply a smaller addressable market?
- Extend the model with demand forecasting to plan inventory and staffing ahead of the winter volume dip

---

**Author:** William Andrés Bernal Sosa — [GitHub](https://github.com/williambernal-data)
