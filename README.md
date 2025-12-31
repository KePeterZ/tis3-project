# Time Series Analysis `TIS3` Capstone Project – Electricity Price Forecasting for EU AI Datacenter Site Selection

## Project Overview

This project forecasts daily wholesale electricity prices in selected European countries to support **cost- and risk-aware site selection** for a new AI data center.

Electricity is a major driver of datacenter operational expenditure (OpEx), and price uncertainty directly translates into planning and budgeting risk.
The goal is therefore not only to forecast prices, but to **turn forecasts into a decision tool**.

The project delivers an **end-to-end forecasting pipeline**, model comparison across multiple approaches, and **daily forecasts with uncertainty for January 2026**.

---

## Business Problem

**Problem**
Forecast daily electricity prices to support cost- and risk-aware selection of an AI data center location in the EU.

**Why this matters**

* Electricity cost is a direct and continuous operational expense
* Forecast uncertainty translates into operational and budgeting risk
* Long-term infrastructure decisions require comparability across locations

---

## Data

* **Source**: Ember dataset from ENTSO-e (European Network of Transmission System Operators for Electricity)
* **Data type**: Daily wholesale electricity prices
* **Time range**: 01.01.2015 – 28.12.2025
* **Countries**:

  * Austria
  * Germany
  * Switzerland
  * France
  * Poland
  * Estonia
* **Forecast horizon**: Daily prices for January 2026

---

## Forecasting Pipeline (CRISP-DM)

The project follows a CRISP-DM-style forecasting pipeline:

1. Business understanding
2. Data preparation and preprocessing
3. Baseline forecasting (naive, weekly seasonal naive)
4. Statistical models (Holt-Winters, AutoARIMA)
5. Machine learning models (Huber Regression)
6. Deep learning benchmark (xLSTM)
7. Model evaluation and selection
8. Final forecasting with uncertainty

---

## Data Engineering

* Extracted country-level electricity price series
* Stored each country as a separate tabular dataset for clarity and efficiency
* Aligned all data to a daily frequency
* Imported and assembled datasets dynamically for modeling and evaluation

---

## Modeling Approach

The goal was to compare **model families**, not just individual methods.

**Models evaluated**

* **Baselines**

  * Naive
  * Weekly seasonal naive
* **Statistical models**

  * Holt-Winters
  * AutoARIMA
* **Machine learning**

  * Huber Regression with lag-based features
* **Deep learning (benchmark)**

  * xLSTM

**Key findings**

* Statistical models did not outperform baselines
* Huber Regression consistently improved performance across countries
* xLSTM did not add predictive value under the given setup and data size

---

## Evaluation

* **Validation strategy**: Time-based validation to avoid information leakage
* **Metrics**:

  * MAE
  * RMSE
  * MAPE (reported, but MAE/RMSE used for selection)
* **Selection criterion**:

  * Consistent out-of-sample improvement relative to baselines

---

## Final Forecast

* The final **Huber Regression model** was retrained on the full dataset
* **Daily electricity prices for January 2026** were forecasted for all countries
* **Uncertainty** was quantified using residual-based prediction intervals

**Forecast output:**
`outputs/jan_2026_electricity_forecasts.csv`

---

## Decision Support & Insights

Forecasts were translated into decision-oriented insights using:

* Expected average prices
* Prediction interval widths (planning risk proxy)
* Upper-bound cost scenarios
* Monthly accumulated OpEx under a 1 MW, 24/7 load assumption

These outputs enable:

* Cost-efficient location comparison
* Risk-aware planning
* Transparent trade-offs between low cost and high uncertainty

---

## Team

* **Peter Keszei**
  Data setup, preprocessing, country-level dataset preparation

* **Mohamed Haroun**
  Modeling, evaluation, forecasting pipeline, model selection, January 2026 forecasts

* **Raphael Suchomel**
  Visualization, interpretation, decision framing, presentation

All team members contributed throughout the project; listed roles indicate areas of primary focus.