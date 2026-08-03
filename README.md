# Retail Sales Performance Analysis

## Overview
This project analyzes five years of retail transaction data to understand business performance and segments customers into actionable groups using RFM analysis. The goal is to determine whether the business is genuinely growing, which factors actually drive profit margin, and where retention effort should focus.

## Dataset
`cleaned_retail_sales.csv` — contains 100,000 retail orders (2019–2023) across 10 Indian states, including customer demographics (Age, City Type), product hierarchy (Category, Sub-Category, Product), order economics (Sales, Profit, Discount, Quantity), shipping details, and a pre-engineered `customer_segment` label.

> **Note:** Place the CSV in a `data/` folder in the repo root (or update the file path in the notebook to match wherever you keep it) before running.

## Approach
1. **Data Cleaning** — standardized column names/types, derived customer age, shipping days, and profit margin %, and validated for nulls/duplicates/invalid values.
2. **Exploratory Data Analysis** — revenue trend, order value and profit distributions, category/regional performance, and discount-vs-margin relationships.
3. **Feature Engineering** — binned `discount` into `discount_band` and `customer_age` into `age_group`, and built an RFM-based `customer_segment`.
4. **Statistical Testing** — one-way ANOVA to check whether state-level sales differences are statistically significant.
5. **Segment Profiling** — customers grouped into four segments (Best Customers, Loyal/High Value, At Risk, Lost/Low Value) based on recency and monetary value, each compared by share of customers vs. share of revenue.
6. **Business Insight** — profit margin compared across discount bands, and revenue concentration compared across customer segments, to identify where the business should focus attention.
7. **Dashboard** — a two-page interactive Power BI dashboard built on top of the cleaned dataset for ongoing monitoring.

## Key Findings
- **Revenue is flat, not growing** — year-over-year change never exceeded ±0.3% across the entire five-year window.
- **State-level differences are not statistically significant** (ANOVA, p = 0.108) — despite a nominal top-3 state ranking, the variation is consistent with random noise.
- **Discounting has a strong, remarkably uniform effect on margin** — roughly an 8 percentage-point drop from the lowest to highest discount band, holding almost identically across all six product categories.
- **Best Customers + Loyal/High Value segments** make up 62.6% of customers but generate 78.1% of revenue — a healthier concentration than the flat customer base might suggest.
- **At-Risk customers still represent 20.3% of revenue** — a meaningful, recoverable retention opportunity before they churn into the Lost/Low-Value segment (1.6% of revenue).

## Conclusion
This analysis paints a picture of a stable, not stagnant-in-a-bad-way, business: revenue holds steady rather than declining, and the customer base skews healthier than the flat top-line numbers alone would suggest, with almost 80% of revenue coming from customers in good standing. The clearest lever for improving profitability isn't regional strategy — the ANOVA result argues against over-indexing there — it's discounting policy, which behaves consistently enough across categories to be managed as a single company-wide decision rather than category-by-category. The next-highest-leverage opportunity is retention-focused: the At-Risk segment is large enough (20.3% of revenue) that even modest improvement there is likely worth more than acquiring new customers at the margins observed in this dataset.

## Tools Used
- Python (pandas, numpy, scipy)
- matplotlib, seaborn (visualization)
- Power BI (interactive dashboard, DAX)

## How to Run
1. Clone this repo.
2. Install dependencies: `pip install -r requirements.txt`
3. Place `cleaned_retail_sales.csv` in a `data/` folder (or adjust the path in the notebook).
4. Open `notebooks/Retail_Sales_Performance.ipynb` in Jupyter or Colab and run all cells.
5. Open `Retail_Sales_Dashboard.pbix` in Power BI Desktop to explore the interactive dashboard.

## Future Improvements
- **Revenue forecasting** — build a time-series model (ARIMA/Prophet) on monthly revenue to move from descriptive to predictive, and test whether the "flat" trend is expected to continue.
- **Cost-benefit quantification** — estimate, in dollar terms, how much margin could be recovered by capping high-discount orders, based on the ~8-point margin gap observed between discount bands.
- **Re-test the regional finding** — check whether the ANOVA result changes with a longer time window or a city-level (rather than state-level) breakdown, since state may be too coarse a grouping to detect a real effect.
- **Predictive retention model** — a classifier trained to flag customers likely to move from At-Risk into Lost/Low-Value before it happens, rather than relying on the static RFM snapshot alone.
- **Interactive exploration app** — a lightweight Streamlit/Plotly Dash layer for filtering by region/category/segment interactively (the Power BI dashboard already serves this need for a business audience, but a lighter web app could serve a portfolio/demo audience).

---

## Author

**Gnyaneswari Dadi**

Aspiring Data Analyst | Business Analytics Enthusiast | Machine Learning Learner

*Full write-up with all charts and detailed findings: [`PROJECT_REPORT.md`](PROJECT_REPORT.md)*
