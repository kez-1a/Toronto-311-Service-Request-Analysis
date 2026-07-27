# Toronto 311 Service Request Analysis

**Beyond the Complaint Count: How Toronto 311 Service Requests Have Changed Over Time**

CIND820 Big Data Analytics Project — Toronto Metropolitan University
Kezia Mathew | Supervisor: Dr. Tamer Abdou

## Project Overview

This project analyzes Toronto 311 customer-initiated service request data to examine how reported
municipal service demand has changed over time. It compares two four-year periods: 2010–2013, the
earliest full-year period available, and 2022–2025, the most recent complete period.

## Research Questions

1. How has reported 311 demand concentration by service request category and city division changed
   between 2010–2013 and 2022–2025?

2. Which high-volume 311 service request categories show different monthly or seasonal patterns
   between 2010–2013 and 2022–2025?

3. Which differences between the early and recent periods can be compared responsibly, and which
   require caution because of changes in categories, divisions, wards, data coverage, or reporting
   practices?
   ----

## Repository Contents

| File | Description |
|---|---|
| `Milestone_4_Final.ipynb` | Final analysis notebook with all outputs saved |
| `Milestone 4 Final Report` | Final report |
| `Milestone_3.ipynb` | Milestone 3 notebook (earlier stage) |
| `Initial_Dataset_Report.ipynb` | Milestone 2 EDA (earlier stage) |
| `requirements.txt` | Package versions |

## Data

Source: [City of Toronto Open Data — 311 Service Requests (Customer Initiated)](https://open.toronto.ca/dataset/311-service-requests-customer-initiated/)
Licence: City of Toronto Open Data Licence

Eight yearly CSV files are needed: `SR2010.csv` through `SR2013.csv`, and `SR2022.csv` through
`SR2025.csv`. Raw files are not included here because of their size (~450 MB).

## IMPORTANT — how the 2022–2025 files must be loaded

The 2010–2013 files are quoted CSVs. **The 2022–2025 files are not.** Any value containing a comma
splits into an extra column, and pandas reports "Expected 9 fields, saw 10".

Using `on_bad_lines="skip"` silently deletes **134,296 rows — 7.5% of the recent period**. The loss is
not random: almost all of it is one division whose name contains a comma
(`Parks, Forestry & Recreation`, renamed `Environment, Climate & Forestry` in 2025).

The notebook includes a `load_recent_file()` function that repairs these rows instead of dropping them.
**Do not replace it with default pandas settings** — doing so produces a materially different result.

## Reproducing the Analysis

1. Download the eight CSV files from the link above
2. Place them in a folder named `CIND 820` in your Google Drive
3. Open `Milestone_4_Final.ipynb` in Google Colab and mount your Drive
4. Runtime → Run all

## Expected Results

Use these to confirm your run matches:

| Check | Expected |
|---|---|
| Total records | 3,027,264 |
| Early period (2010–2013) | 1,232,720 |
| Recent period (2022–2025) | 1,794,544 |
| Unique service request types | 990 |
| Duplicate rows | 2,318 (0.08%) |
| Cramér's V (Period × Division) | 0.3564 |
| Final model MAPE (2025) | 14.86% |

## Methods

- Data repair and integration across eight yearly files
- Data quality audit: missingness, duplicates, date coverage, unique values
- Statistical testing: chi-square with Cramér's V, Shapiro-Wilk, Wilcoxon signed-rank with
  rank-biserial effect size, chi-square goodness of fit with Cohen's w, Spearman correlation
- Comparability audit measuring label overlap and record coverage
- Forecast comparison of four models using rolling-origin backtesting, evaluated with MAE, RMSE,
  MAPE and WAPE, at total and division level

## Environment

Python 3 (Google Colab). pandas, numpy, matplotlib, seaborn, scipy, statsmodels, scikit-learn.

## Limitations

Findings are patterns in reported 311 demand, not proof of actual municipal need. The open dataset
represents roughly 30–35% of total 311 activity and covers 6 of 45 divisions. Ward-level comparisons
are not made because only 2 ward values are shared across the periods.
