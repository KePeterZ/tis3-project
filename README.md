# TIS3 Capstone Project – Electricity Price Forecasting

## Project Overview
This project forecasts daily electricity prices in selected EU countries to support
the decision of locating a new AI data center based on energy cost and risk.

The focus is on building an end-to-end forecasting pipeline using open, dynamic data,
and comparing statistical, machine learning, and deep learning models.

## Data
We use daily wholesale electricity prices from 01.01.2015 to 28.12.2025 for:
Austria, Germany, Switzerland, France, Poland, and Estonia.

The data is publicly available and updated continuously.

## Forecasting Pipeline
The project follows a CRISP-DM style forecasting process:
- Business understanding
- Data preparation and preprocessing
- Baseline forecasting (naive, seasonal naive)
- Statistical models (Holt-Winters, AutoARIMA)
- Machine learning models (Huber Regression)
- Deep learning models (xLSTM)
- Model evaluation and selection
- Final forecasting with uncertainty

## Model Selection
Baseline and statistical models provided strong reference performance.
Huber Regression consistently outperformed baselines across countries.

Deep learning (xLSTM) was evaluated but did not improve predictive accuracy
for this dataset and was therefore not selected as the final model.

## Final Forecast
The final model (Huber Regression) was retrained on the full dataset and used
to forecast daily electricity prices for January 2026.

Uncertainty is quantified using residual-based prediction intervals.

Forecasts are available in:
outputs/jan_2026_electricity_forecasts.csv

## Value and Decision Support
Accurate electricity price forecasts support:
- Cost estimation for data center operations
- Risk-aware comparison of candidate locations
- Better planning under price uncertainty

Higher forecast uncertainty directly translates into higher operational risk,
which is critical when selecting a long-term infrastructure location.

## Team
- Peter: Set up and Data Preprocessing
- Mohamed: Modeling, Evaluation, Forecasting Pipeline
- Raphael: Visualization and Presentation