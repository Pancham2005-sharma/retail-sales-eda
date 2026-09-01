# Retail Sales — EDA & Data Cleaning

Exploratory data analysis and data quality audit on a retail sales dataset, following a structured 4-phase process: load and inspect, clean, detect and treat outliers, then summarize with business insights.

**Dataset:** `retail_sales_dataset.csv` (Kaggle) — 1,000 rows, 9 columns

## Data Quality Report
- **Missing values:** 0 across all columns
- **Duplicate rows:** 0
- **Type fix:** converted `Date` from string to proper datetime
- **Outliers:** 32 rows (3.2%) flagged via the IQR method, applied per product category — all 32 fell in the Clothing category, driven by items priced at the category's Rs. 500 ceiling combined with higher quantities (3–4 units). **Decision: retained** — these are genuine premium purchases, not data entry errors (no negative values, no impossible numbers found)

## Business Insights
- **Category performance:** Electronics and Clothing drive the most revenue; Beauty lags noticeably behind — worth investigating whether Beauty is underpriced or under-marketed
- **Seasonality:** clear monthly pattern with sales peaks in May and October — useful for planning inventory and promotions around those months
- **Demographics:** spending is consistent across gender and age groups — no single demographic dominates, suggesting the customer base has broad appeal rather than being niche
- **What drives revenue:** Total Amount correlates far more strongly with item price (0.85) than with quantity purchased (0.37) — customers are buying higher-priced individual items, not bulk-buying

## Tech Stack
Python, pandas, matplotlib, seaborn, IQR-based outlier detection

## Folder Structure
```
├── Retail_Sales_EDA_PanchamSharma.ipynb
├── data/
│   └── retail_sales_dataset.csv
└── README.md
```

## How to Run
```bash
pip install pandas matplotlib seaborn jupyter
jupyter notebook Retail_Sales_EDA_PanchamSharma.ipynb
```
Run all cells top to bottom (Kernel → Restart & Run All recommended for a clean state).

## Limitations
- Dataset was already clean on import (no missing values, no duplicates) — this project demonstrates a thorough EDA process more than it demonstrates messy-data cleanup skills
- Outlier retention was a judgment call based on category-level pricing logic; a stricter or more automated pipeline might flag these differently
- Seasonality and demographic insights are descriptive, not causal — useful for planning but not a substitute for controlled testing (e.g. of pricing or marketing changes)
