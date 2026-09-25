# Precision Agriculture & NumPy Numerical Analysis

## Overview

This project covers four distinct numerical analysis modules:

1. **Business Analytics - Sales Performance Calculator**
   * Vectorized sales adjustments (+10% hypothetical revenue scaling).
   * Comparative analysis between total revenue volume and daily average baselines.

2. **Education Analytics - Student Performance & Variance**
   * Manual calculation of mean score, deviations, and sum of squared deviations.
   * Step-by-step mathematical breakdown of standard deviation.

3. **Engineering & Scientific Computing - Trigonometric Series Convergence**
   * Calculation of terms for the series $\frac{\sin(k \cdot \theta)}{k}$ in radians.
   * Empirical analysis of series convergence as $k$ scales from $99$ to $9,999$ terms.

4. **Bonus Challenge - Maize Farm Irrigation & Yield Efficiency**
   * Real-world agricultural decision support model tracking a 10-day heatwave.
   * Calculates daily soil moisture loss (evaporation rate), soil moisture deficits below the critical 35% threshold, and required replenishment irrigation volumes.

---

## About the Maize Farm Irrigation & Yield Efficiency Project

During periods of high temperature and heatwaves, maintaining optimal soil moisture levels is critical to prevent crop heat stress, which inhibits physiological and photosynthetic processes in maize. However, over-irrigating can lead to soil nutrient leaching and wasted water resources.

This project processes a 10-day dataset of ambient temperatures and soil moisture levels to deliver an actionable, data-driven irrigation strategy. It calculates daily evaporation rates, identifies critical moisture deficit periods, and computes the exact volume of top-up irrigation required to maintain a healthy threshold.

## Objective

To provide farm management with an actionable, daily irrigation schedule that prevents maize crop heat stress, optimizes water usage, and avoids over-irrigation that leads to soil nutrient leaching.

* **Prevent Crop Heat Stress:** Monitor soil moisture to ensure levels do not drop below the critical 35% moisture threshold.
* **Optimize Water Resources:** Calculate top-up irrigation volumes based only on actual soil moisture deficits rather than applying unnecessary fixed watering cycles.
* **Avoid Nutrient Leaching:** Eliminate over-irrigation on days where soil moisture is already saturated.
* **Identify Peak Stress Days:** Pinpoint peak temperature days using array indexing to prepare for extreme weather events.

## Data & Methodology

### Dataset Specs (10-Day Window)

* `days`: Sequence of 10 observation days.
* `temperatures`: Daily ambient max temperatures in Celsius.
* `moisture_array`: Initial daily soil moisture levels prior to evaporation.

### Key Analytical Logic & Calculations

* **Daily Moisture Drop (Evaporation Rate):** Calculated using vector slicing (`np.subtract(moisture_array[:-1], moisture_array[1:])`) to determine day-over-day moisture loss.
* **Moisture Deficit:** Calculated against an ideal threshold. Negative deficits (days where soil moisture exceeds threshold) are clamped to 0 using `np.maximum(0, deficit)` to reflect zero required irrigation.
* **Irrigation Volume Required:** Based on the domain assumption that moisture deficit below threshold requires irrigation water per unit area.
* **Hottest Day Identification:** Uses `np.max()` for peak temperature retrieval and `np.argmax()` to locate the exact day index.

## Key Results & Findings

### Insights

* **Days 1–4:** Soil moisture remains at or above the threshold. 0 Liters of irrigation required.
* **Day 6 (Peak Heatwave):** Reached a peak temperature, causing rapid soil drying.
* **Days 5–10:** Moisture consistently fell below threshold, peaking at a deficit on Day 8, requiring immediate scheduled replenishment.

## Python Concepts Used

* **NumPy Vectorization:** Element-wise array math without explicit `for` loops
* **Array Differences:** `np.diff()` for calculating sequential daily rate changes
* **Thresholding & Clipping:** `np.maximum()` to eliminate negative deficit values
* **Scaling & Broadcasting:** Vectorized multiplication (`np.multiply()`) for volume conversion
* **Statistical Extrema & Indexing:** `np.max()` and `np.argmax()` to isolate environmental extremes
* **Trigonometrics & Sequences:** `np.radians()`, `np.sin()`, and `np.arange()`

## Key Features

* **Automated Water Management:** Zero-irrigation logic for days above the 35% moisture threshold to conserve water and protect soil nutrients.
* **Vectorized Data Processing:** Fast, loopless numeric calculations across multi-day environmental datasets.
* **Agronomic Decision Support:** Direct conversion of raw environmental data (temperature & moisture) into actionable volume metrics for farm operators.

## Technologies Used

* **Language:** Python 3.13
* **Libraries:** NumPy, Jupyter Notebook
* **Environment:** Anaconda / Jupyter
* **Version Control:** Git, GitHub

## Conclusion

This project demonstrates how basic numerical computing with NumPy can transform raw field data into actionable agricultural decisions. Farm managers can integrate this logic into automated drip-irrigation systems to optimize water use, protect crop yields, and maintain soil health.

## Author

Peter O. Oyanoghafo  
LinkedIn: [peteroyanoghafo](https://www.linkedin.com/in/peteroyanoghafo)
