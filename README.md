# Forecasting Sustainable Aviation Energy: Green Hydrogen & SAF Production

**NASA Glenn Research Center – Graphics & Visualization Lab**

---

## Overview

This project explores future trends in **sustainable aviation energy**, focusing on:

* Green Hydrogen production (forecasted to 2050 using LSTM)
* Sustainable Aviation Fuel (SAF) production (forecasted using SARIMA)

The goal is to understand how clean aviation energy sources may evolve and support decarbonization of the aviation sector.

---

## Objectives

* Forecast green hydrogen production up to 2050
* Model SAF production trends using time series analysis
* Compare machine learning (LSTM) vs statistical (SARIMA) forecasting approaches
* Analyze growth patterns and long-term sustainability constraints

---

## Datasets

### 1. Green Hydrogen (IEA Dataset)

* International Energy Agency Green Hydrogen Projects dataset
* Includes project-level hydrogen production capacity and timelines
* Key feature: **MW equivalent production**

### 2. SAF Production (EPA Dataset)

* U.S. Environmental Protection Agency Renewable Fuel Standard (RINs dataset)
* Focused on Non-Ester Renewable Diesel (SAF proxy)
* Aggregated to annual time series values

---

## Methodology

### Green Hydrogen Forecasting (LSTM Model)

* Data filtering: Dedicated renewable hydrogen projects only
* Unit standardization → MW equivalent
* Aggregated yearly time series
* Scaling using mean & standard deviation normalization
* Lag-based sequence generation (12-step windows)
* Model: 2-layer **stateful LSTM neural network**

  * Dropout layers (50%) to reduce overfitting
  * Adam optimizer
  * MAE loss function

**Output:** Forecasted hydrogen production trends through 2050

---

### SAF Forecasting (SARIMA Model)

* Time series aggregation from monthly to annual values
* Data transformations:

  * Box-Cox transformation
  * Log transformation
* Differencing:

  * Seasonal (lag 12)
  * Trend (lag 1)
* Model selection via AICc comparison
* Final model: **SARIMA(1,1,2)(1,1,1)[12]**

---

## Key Results

### Green Hydrogen (LSTM)

* Strong exponential growth from 2020–2047
* Growth stabilizes around ~3200–3300 MW by 2050
* Indicates long-term saturation due to infrastructure and resource constraints

### ✈️ SAF (SARIMA)

* Captures seasonal + downward trend behavior
* Forecast shows gradual stabilization with uncertainty bounds
* Reflects regulatory, economic, and production constraints

---

## Key Insights

* Green hydrogen shows **rapid long-term exponential growth with plateauing**
* SAF production shows **slower, constrained stabilization**
* Hydrogen appears more scalable long-term than SAF
* Both fuels show **infrastructure-limited growth trajectories**
* Forecast uncertainty increases significantly over long horizons

---

## Tools & Libraries

### R (SAF Model)

* `forecast`, `tseries`, `ggplot2`

### Python (LSTM Model)

* `Keras`, `TensorFlow`, `NumPy`, `Pandas`, `Matplotlib`

---

## Conclusion

This project demonstrates how different modeling approaches capture energy transition trends:

* LSTM effectively models nonlinear long-term growth in hydrogen production
* SARIMA captures seasonal and trend-based behavior in SAF production

Together, they provide insights into the future of **sustainable aviation energy systems** and highlight both the potential and limitations of clean fuel adoption.

---

## Data Sources

* International Energy Agency (IEA) – Green Hydrogen Projects Dataset
  [https://www.iea.org/](https://www.iea.org/)
* U.S. EPA Renewable Fuel Standard (RINs Dataset)
  [https://www.epa.gov/](https://www.epa.gov/)

---

## Future Work

* Integrate hydrogen + SAF into a unified aviation energy model
* Add external drivers (policy, cost, infrastructure constraints)
* Explore hybrid models (LSTM + SARIMA)
* Incorporate spatial + regional forecasting
