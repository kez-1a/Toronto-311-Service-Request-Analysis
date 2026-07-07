# Toronto 311 Service Request Analysis
This project analyzes Toronto 311 customer-initiated service request data to examine how reported municipal service demand has changed over time.

## Project Overview

This project analyzes Toronto 311 customer-initiated service request data to examine how reported municipal service demand has changed over time. The analysis compares two four-year periods: 2010–2013 and 2022–2025.

## Tools Used

- Python
- pandas
- SweetViz
- Power BI (optional)

## Dataset

The dataset used is the City of Toronto’s 311 Service Requests – Customer Initiated.

Years included:
- 2010, 2011, 2012, 2013
- 2022, 2023, 2024, 2025


## Repository Contents

- Python notebook for data loading, profiling, cleaning, and EDA
- Data source notes
- Summary tables and charts
- Final report files
- Optional Power BI visuals

## Reproducibility

To reproduce the analysis, download the yearly CSV files from the City of Toronto Open Data Portal, place them in the same folder used in the notebook and click 'Run All' in python.

## Limitations

The findings are interpreted as patterns in reported 311 demand, not as proof of actual municipal need.


## Milestone 3 UPDATE

This repository now includes the Milestone 3 notebook for the Toronto 311 analysis project. The notebook includes data loading, integration, feature engineering, data quality checks, exploratory data analysis, Pareto analysis, heatmap visualizations, and a simple baseline monthly prediction model. The baseline model uses 2022–2024 monthly request counts to predict 2025 monthly request counts. The model was evaluated using MAE, RMSE, and MAPE. Raw data files are not included in this repository due to file size. They can be downloaded from the City of Toronto Open Data Portal.


The analysis compares two four-year periods:
- Early Period: 2010–2013
- Recent Period: 2022–2025

The Milestone 3 notebook includes:
- data loading and integration
- creation of `Source Year` and `Period` fields
- conversion of `Creation Date` into datetime format
- creation of `Year`, `Month`, `Month Name`, `Weekday`, and `Season` fields
- missing value review
- duplicate check
- unique value summary
- service request type analysis
- division-level analysis
- monthly and seasonal analysis
- Pareto / cumulative share analysis
- heatmap of monthly patterns by top service request types
- baseline monthly prediction model
- model evaluation using MAE, RMSE, and MAPE

The baseline model uses monthly request counts from 2022, 2023, and 2024 to predict actualmonthly request counts for 2025. This setup avoids leakage because the actual 2025 values are only used for testing and evaluation.
