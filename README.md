# Seasonal Revenue Forecasting with Regression Analysis

A regression-based forecasting project that models the relationship between production volume and revenue, using seasonal dummy variables and interaction terms to test whether seasonality (Fall vs. Spring) improves forecast accuracy.

## Overview

This project builds and compares two multiple linear regression models to forecast revenue from production data:

- **Model 1:** Production + Fall dummy variable + Fall interaction term
- **Model 2:** Production + Spring dummy variable + Spring interaction term

Each model is trained on a historical dataset and evaluated on a held-out test set using **Mean Absolute Percentage Error (MAPE)** to determine which seasonal specification produces more accurate forecasts.

## Methodology

1. **Data preparation** — Loaded historical production/revenue data and converted dates to datetime format.
2. **Dummy variable creation** — Flagged observations falling in Spring (Mar–May) or Fall (Sep–Nov) with binary indicators.
3. **Interaction terms** — Multiplied production by each seasonal dummy to allow the production-revenue slope to differ by season.
4. **Model fitting** — Fit OLS regressions (via `statsmodels`) on the training split for each seasonal specification.
5. **Model evaluation** — Generated predictions on the test split and computed MAPE for each model.
6. **Visualization** — Plotted actual vs. fitted revenue lines by season, and compared MAPE scores across models.

## Results

| Model | Specification | MAPE |
|---|---|---|
| Model 1 | Production + Fall dummy + interaction | 22.02% |
| Model 2 | Production + Spring dummy + interaction | 28.93% |

**Recommendation:** Model 1 (Fall-based forecast) is the stronger model, with a lower MAPE, and is recommended for seasonal revenue forecasting. Suggested next steps include testing models that combine multiple seasons or incorporate additional variables (e.g., cooling/heating degree days) alongside the seasonal dummies.

## Tech Stack

- Python
- pandas, numpy
- statsmodels (OLS regression)
- matplotlib (visualization)

## Files

- `AFM244_Week10_Quiz.ipynb` — Full analysis notebook, including data preparation, model fitting, evaluation, and a written recommendation memo.

## Notes

This project was completed as part of AFM 244 (Intermediate Financial Accounting with Data Analytics). Data used is coursework-provided sample data (`AICPA_regressionAnalysisData.csv`) and is illustrative rather than real company financials.
