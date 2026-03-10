# bmw-sales-powerbi-dashboard
Power BI dashboard analyzing BMW sales (2018–2025) by time, region, and model
## Overview
This project analyzes BMW sales performance from **2018 to 2025** across **regions** and **models** using an interactive **Power BI** report.  
The main goals are to understand:
- How **units sold** and **revenue** evolve over time
- **Seasonality** patterns (month-of-year)
- Which **regions** drive volume
- Which **models** lead by **units** vs **revenue**
- How sales distribution varies across **Region × Model** (heatmap)

---

## Dataset
**Columns**
- Time: `Year`, `Month`, `YearMonth`
- Dimensions: `Region`, `Model`
- Metrics: `Units_Sold`, `Revenue_EUR`, `Avg_Price_EUR`
- Additional drivers: `BEV_Share`, `Premium_Share`, `GDP_Growth`, `Fuel_Price_Index`

**Granularity:** monthly (`YearMonth`), split by `Region` and `Model`.

> Note: Dataset is not included in this repository (licensing/privacy constraints).  

---

## Data Model
The report is built with a **star schema**:
- **FactSales**: main fact table (units sold, revenue, price)
- **DimDate**: monthly date dimension for time analysis
- **DimRegion**: region dimension
- **DimModel**: model dimension

To guarantee correct month ordering in visuals, the model includes a `MonthLabel` field (e.g., `01 Jan`, `02 Feb`, …).

---

## Measures (DAX)
Core measures used across the report:
- **Total Units** = sum of units sold  
- **Total Revenue** = sum of revenue (EUR)  
- **Avg Price (Weighted)** = `Total Revenue / Total Units` (weighted average price)

---

## Report Pages
### 01_Overview
High-level performance:
- KPIs: Total Units, Total Revenue, Weighted Avg Price
- Units & Revenue by Year
- Annual units trend by region

### 02_Time
Time-focused analysis:
- Monthly trends (YearMonth)
- Seasonality (Jan–Dec) comparing selected years

### 03_Regions
Regional comparison:
- Total units by region (ranking)
- Units by year and region

### 04_Models
Model performance:
- Top models by units
- Top models by revenue
- Heatmap: units by region and model

---

## Key Insights
- **Total revenue is €1.57T** across the full period (2018–2025).
- The **top model by units sold is the iX**, while the **top model by revenue is the X7** — volume leadership and revenue leadership differ.
- **China is the top region by total units**, leading overall demand compared to Europe, USA, and Rest of World.

---

## How to Use
1. Download the `.pbix` file (see repository files or link below if GitHub size limits apply).
2. Open it with **Power BI Desktop**.
3. Navigate through pages and use slicers (Year / Region / Model) to explore the data.

---

## Repository Structure
- `BMW SALES.pbix` — Power BI report  
- `README.md` — project documentation  
- `images/` — report screenshots (recommended)

---

## Next Improvements
- Add **YoY%** measures for units and revenue (Year-over-Year growth)
- Add a “Drivers” page using BEV/Premium/GDP/Fuel variables
- Improve UX with synced slicers across pages + a “Reset filters” button
