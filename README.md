# Airbnb Listings Data Analysis (NYC)

End-to-end analysis of ~102,000 Airbnb listings in New York City, exploring what drives pricing, demand, and host behavior. The project was built across three tools, each used for what it's best at: **Python** for cleaning and exploratory analysis, **Advanced Excel** for KPI reporting and pivot-based business analysis, and **Tableau** for an interactive visual dashboard.

## Project Overview

Raw Airbnb listing data is messy — inconsistent formatting, missing values, wrong data types, and duplicate records. This project takes that raw data and turns it into a clean, analysis-ready dataset, then answers a core business question:

**What factors influence Airbnb listing performance and pricing in NYC?**

The same cleaned dataset feeds all three deliverables, so the findings stay consistent whether you're looking at the notebook, the workbook, or the dashboard.

## Dataset

- **Source:** NYC Airbnb Open Data
- **Size:** ~102,000 listings, 22+ columns
- **Key fields:** price, service fee, room type, neighbourhood / neighbourhood group, number of reviews, review rate, host details, minimum nights, availability, cancellation policy

## Tools & Workflow

### 1. Python (Pandas, NumPy, Matplotlib, Seaborn)

Used for data cleaning and exploratory data analysis in `airbnb_analysis.ipynb`.

**Data Cleaning**
- Standardized column names (lowercase, stripped, underscored)
- Cleaned `price` and `service_fee` columns — stripped `$` and `,` characters, converted to numeric, imputed missing values with the median
- Filled missing categorical data (`host_name`, `host_identity_verified`) with sensible defaults instead of dropping rows
- Dropped columns with >50% missing data (`license`, `house_rules`, `reviews_per_month`)
- Removed duplicate records
- Corrected data types, including converting `last_review` to datetime
- Exported the cleaned dataset (`Airbnb_Cleaned.csv`) as the single source of truth for Excel and Tableau

**Exploratory Data Analysis**
- Distribution of listings by room type
- Average price by neighbourhood group and by room type
- Listing volume by neighbourhood group
- Top 10 hosts by number of listings
- Correlation heatmap across numeric variables
- Price distribution by room type (boxplot)
- Top 10 most expensive neighbourhoods
- Price vs. number of reviews (scatter plot)

**Key Insights from the Notebook**
- Entire homes/apartments are the most common listing type and also command the highest average prices; shared rooms are the most affordable
- Listings are concentrated in a handful of neighbourhood groups, showing clear geographic demand patterns
- Price is right-skewed — most listings are moderately priced, with a smaller number of luxury outliers pulling the average up
- A small number of hosts manage a disproportionate share of listings, pointing to professional/commercial hosting alongside individual hosts
- Numeric variables show only weak-to-moderate correlation with price, meaning no single factor drives pricing — it's a mix of location, room type, and listing quality

### 2. Advanced Excel/Google Sheets

Built a structured, multi-sheet workbook (`AIRBNB_ANALYSIS.xlsx`) on top of the cleaned data, designed to be explored by a non-technical stakeholder.

- **`Airbnb_Cleaned`** — the full cleaned dataset (~102K rows), the base layer for every formula and pivot in the workbook
- **`Power_query`** — data shaped and loaded using Power Query for repeatable transformation
- **`Analysis`** — a KPI summary and formula-driven business analysis layer, including:
  - Headline KPIs: total listings, average price, median price, average service fee, average rating, total reviews
  - **XLOOKUP** to pull metrics dynamically for a selected room type
  - **Dynamic array formulas** to surface the top 10 highest-priced neighbourhoods on the fly
- **`pivot_analysis`** — six PivotTables breaking the data down by:
  1. Pricing by room type
  2. Neighbourhood group performance (listings, price, reviews, rating)
  3. Customer engagement by room type (reviews and ratings)
  4. Cancellation policy vs. pricing
  5. Price category vs. room type (cross-tab of listing counts)
  6. Price category vs. neighbourhood group (cross-tab of listing counts)

This layer turns the raw analysis into something a manager could open and filter without touching a line of code.

### 3. Tableau Dashboard

An interactive single-page dashboard (`Airbnb_dashboard_twbx.twb`) combining KPI cards, a geographic map, and multiple chart types for at-a-glance exploration:

- **KPI cards** — headline metrics (listings, average price, ratings) surfaced as text cards
- **Map view** — listings plotted geographically (circle marks) to visualize density and pricing by location across NYC boroughs
- **Pie chart** — listing share by room type
- **Bar chart** — pricing/volume comparisons across categories
- **Supporting views** — additional breakdowns for neighbourhood and pricing trends

The dashboard lets a viewer filter and drill into the same insights from the notebook and workbook, but visually and interactively.

## Key Business Insights

| Insight | Detail |
|---|---|
| Room type drives price | Entire homes/apartments have the highest average price (~$625); shared rooms are cheapest |
| Location matters | Neighbourhoods like New Dorp, Chelsea (Staten Island), and Fort Wadsworth top the price rankings, well above the city-wide average |
| Demand is concentrated | Manhattan and Brooklyn together account for the majority of listings |
| Hosting is uneven | A small set of hosts manage multiple properties — a sign of professional/commercial activity in the market |
| Reviews ≠ price | Review count and rating show only weak correlation with price — quality signals don't strongly predict cost |
| Cancellation policy has minimal price impact | Flexible, moderate, and strict policies show nearly identical average pricing |

## Repository Structure

```
├── airbnb_analysis.ipynb        # Python data cleaning + EDA
├── Airbnb_Cleaned.csv           # Cleaned dataset (output of the notebook)
├── AIRBNB_ANALYSIS.xlsx         # Excel/Sheets workbook: KPIs, XLOOKUP, dynamic arrays, PivotTables
├── Airbnb_dashboard_twbx.twb    # Tableau dashboard
└── README.md
```

## Tech Stack

`Python` · `Pandas` · `NumPy` · `Matplotlib` · `Seaborn` · `Jupyter Notebook` · `Google Sheets (Power Query, XLOOKUP, Dynamic Arrays, PivotTables)` · `Tableau`

## Author


Khushi Baliyan
[GitHub](https://github.com/kbaliyan85) · [LinkedIn](https://linkedin.com/in/khushi-baliyan)
