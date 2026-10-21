
# Delivery Operations & Delay Analysis

A data analysis project focused on identifying delivery delays and understanding operational bottlenecks in a last-mile delivery platform using Python, Pandas, and NumPy, with Tableau planned for visualization.

## Project Overview

Delivery delays can reduce customer satisfaction and operational efficiency. The main goal of this project is to investigate where delays occur and whether they are associated with order preparation, transportation, traffic conditions, or peak-hour demand.

Using a real-world delivery dataset, the project transforms raw records into structured data that can be used to analyze delivery performance and support data-driven operational decisions.

## What I Did in the Code

### 1. Data Cleaning and Validation
I used Pandas to inspect the dataset, identify missing or invalid values, and clean timestamp-related fields. This step helps ensure that delivery records are reliable enough for time-based calculations.

### 2. Outlier Handling
I identified and handled outliers that could distort delivery-time analysis. The purpose was to reduce the impact of unusual or unreliable records while preserving meaningful delivery patterns.

### 3. Feature Engineering
I created new time-based features to analyze the different stages of the delivery process:

- **Prep Time:** The time spent preparing an order, based on the available order and pickup timestamps.
- **Transit Time:** The time between order pickup and delivery, calculated using the available timestamps.
- **Total Delivery Time:** The overall delivery duration, used to evaluate delivery performance.

These features help distinguish preparation-related delays from transportation-related delays instead of treating the entire delivery process as a single time measurement.

### 4. Time-of-Day Categorization
I grouped orders into time-of-day categories, such as **Lunch Peak** and **Dinner Rush**. This makes it possible to compare delivery performance across different periods and investigate whether peak-hour demand is associated with longer delivery times.

### 5. Delayed-Order Identification
I created a delay flag to distinguish delayed orders from non-delayed orders based on a defined delay criterion. This allows delayed orders to be counted, compared, and analyzed across different time periods and operational conditions.

## Key Questions

- Is preparation time or transit time contributing more to delivery delays?
- Do lunch and dinner peak periods experience longer delivery times?
- How are weather and traffic conditions associated with delivery performance?
- Does delivery performance vary by vehicle type or condition?
- What patterns distinguish delayed orders from on-time orders?

## Tools & Technologies

- **Python** — Data processing and analysis
- **Pandas** — Data cleaning, manipulation, and feature engineering
- **NumPy** — Numerical operations and data processing
- **Tableau Public** — Planned interactive dashboard development

## Project Workflow

1. Inspect and clean the raw delivery dataset.
2. Handle missing values, invalid timestamps, and outliers.
3. Calculate preparation, transit, and total delivery times.
4. Create time-of-day categories and flag delayed orders.
5. Export the cleaned dataset to CSV.
6. Build an interactive Tableau dashboard to explore delay hotspots, peak-hour bottlenecks, and vehicle performance.

## Project Status

- [x] Data cleaning and validation
- [x] Outlier handling
- [x] Feature engineering
- [x] Time-of-day categorization
- [x] Delayed-order identification
- [ ] Export final cleaned dataset to CSV
- [ ] Build and publish the Tableau Public dashboard

## Expected Outcome

The project aims to produce a clean, analysis-ready dataset and an interactive dashboard that reveal delivery delay patterns and help identify areas where operational improvements may be needed.