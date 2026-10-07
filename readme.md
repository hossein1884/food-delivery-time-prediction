# Food Delivery Time Prediction

A complete Data Science and Machine Learning project for analyzing food delivery data and predicting the time required to deliver an order.

This project uses real-world food delivery data containing information about delivery personnel, restaurants, customers, weather conditions, traffic density, vehicle conditions, order types, locations, festivals, and other factors that can influence delivery time.

The main objective is to understand the factors affecting delivery duration, prepare and clean the dataset, perform exploratory data analysis, and build a machine learning pipeline capable of predicting the expected delivery time of an order.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Problem Statement](#problem-statement)
- [Project Objectives](#project-objectives)
- [Dataset](#dataset)
- [Dataset Features](#dataset-features)
- [Target Variable](#target-variable)
- [Project Workflow](#project-workflow)
- [Data Preprocessing](#data-preprocessing)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Feature Engineering](#feature-engineering)
- [Machine Learning](#machine-learning)
- [Model Evaluation](#model-evaluation)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Usage](#usage)
- [Expected Outcome](#expected-outcome)
- [Future Improvements](#future-improvements)
- [Conclusion](#conclusion)

---

## Project Overview

Food delivery time is affected by multiple factors.

For example, an order placed during heavy traffic in a metropolitan area may take significantly longer to deliver than an order placed during low traffic in an urban area.

Similarly, weather conditions, delivery distance, vehicle condition, the number of simultaneous deliveries, and the type of order can all influence the final delivery time.

This project analyzes these factors using a real-world food delivery dataset and develops a machine learning solution for estimating delivery time.

The project follows a complete data science workflow:

```text
Raw Dataset
     |
     v
Data Loading
     |
     v
Data Cleaning
     |
     v
Missing Value Handling
     |
     v
Outlier Detection
     |
     v
Exploratory Data Analysis
     |
     v
Feature Engineering
     |
     v
Feature Encoding
     |
     v
Train / Test Split
     |
     v
Machine Learning Model
     |
     v
Model Evaluation
     |
     v
Delivery Time Prediction
```

---

# Problem Statement

The goal of this project is to predict the amount of time required to deliver a food order.

The target variable is:

```text
Time_taken(min)
```

The model receives information about an order and its delivery conditions and attempts to estimate the delivery duration in minutes.

For example, the dataset may contain information such as:

- Delivery person's age
- Delivery person's rating
- Restaurant location
- Customer location
- Order date
- Order time
- Weather condition
- Traffic density
- Vehicle condition
- Type of order
- Type of vehicle
- Number of multiple deliveries
- Festival status
- City type

Using these features, the machine learning model learns patterns from historical delivery records.

---

# Project Objectives

The main objectives of this project are:

1. Understand the structure of the food delivery dataset.
2. Clean and prepare raw data for machine learning.
3. Detect and remove invalid or inconsistent records.
4. Handle missing values.
5. Detect and remove statistical outliers.
6. Analyze relationships between delivery time and different features.
7. Extract useful information from date and time columns.
8. Convert categorical variables into numerical representations.
9. Build machine learning models for delivery-time prediction.
10. Evaluate model performance using appropriate regression metrics.
11. Identify the most important factors affecting delivery time.
12. Create a clean and reproducible machine learning workflow.

---

# Dataset

The project uses a dataset named:

```text
train.csv
```

The dataset contains historical food delivery records.

A simplified example of the dataset structure is:

| ID | Delivery_person_ID | Age | Rating | Weather | Traffic | Vehicle | City | Time Taken |
|---|---|---:|---:|---|---|---|---|---:|
| 0x4607 | INDORES13DEL02 | 37 | 4.9 | Sunny | High | Motorcycle | Urban | 24 |
| 0xb379 | BANGRES18DEL02 | 34 | 4.5 | Stormy | Jam | Scooter | Metropolitian | 33 |
| 0x5d6d | BANGRES19DEL01 | 23 | 4.4 | Sandstorms | Low | Motorcycle | Urban | 26 |
| 0x7a6a | COIMBRES13DEL02 | 38 | 4.7 | Sunny | Medium | Motorcycle | Metropolitian | 21 |
| 0x70a2 | CHENRES12DEL01 | 32 | 4.6 | Cloudy | High | Scooter | Metropolitian | 30 |

The original dataset contains both numerical and categorical variables.

---

# Dataset Features

The dataset contains the following columns.

## 1. ID

A unique identifier for each delivery record.

Example:

```text
0x4607
0xb379
0x5d6d
```

This field is mainly useful for identifying records and generally should not be used as a predictive feature.

---

## 2. Delivery_person_ID

Identifier of the delivery person.

Example:

```text
INDORES13DEL02
BANGRES18DEL02
```

This feature can potentially be used to analyze delivery-person-specific behavior, although its suitability for direct model training should be evaluated carefully.

---

## 3. Delivery_person_Age

Age of the delivery person.

Example:

```text
37
34
23
38
32
```

This is a numerical feature.

---

## 4. Delivery_person_Ratings

Customer rating received by the delivery person.

Example:

```text
4.9
4.5
4.4
4.7
4.6
```

This is a numerical feature that may provide information about delivery performance.

---

## 5. Restaurant_latitude

Latitude coordinate of the restaurant.

---

## 6. Restaurant_longitude

Longitude coordinate of the restaurant.

---

## 7. Delivery_location_latitude

Latitude coordinate of the delivery destination.

---

## 8. Delivery_location_longitude

Longitude coordinate of the delivery destination.

The restaurant and delivery coordinates can potentially be combined to calculate the approximate delivery distance.

---

## 9. Order_Date

Date on which the order was placed.

Example:

```text
19-03-2022
25-03-2022
05-04-2022
```

This feature can be transformed into useful components such as:

- Day
- Month
- Day of week

---

## 10. Time_Orderd

Time at which the order was placed.

Example:

```text
11:30:00
19:45:00
08:30:00
```

This feature can be transformed into:

- Hour
- Minute
- Time period
- Morning / Afternoon / Evening / Night

---

## 11. Time_Order_picked

Time at which the delivery person picked up the order.

Example:

```text
11:45:00
19:50:00
08:45:00
```

The difference between `Time_Orderd` and `Time_Order_picked` may provide an important feature representing preparation or pickup delay.

---

## 12. Weatherconditions

Weather condition during the delivery.

Possible values include:

```text
Sunny
Cloudy
Stormy
Sandstorms
Fog
Windy
```

Weather can significantly affect delivery time.

---

## 13. Road_traffic_density

Traffic level during the delivery.

Possible values include:

```text
Low
Medium
High
Jam
```

This is expected to be one of the important variables affecting delivery duration.

---

## 14. Vehicle_condition

Condition of the delivery vehicle.

Example values:

```text
0
1
2
```

The vehicle condition may influence delivery performance.

---

## 15. Type_of_order

Type of food order.

Examples:

```text
Snack
Drinks
Buffet
Meal
```

Different order types may require different preparation and handling times.

---

## 16. Type_of_vehicle

Vehicle used for delivery.

Examples:

```text
Motorcycle
Scooter
Electric_scooter
Bicycle
```

Vehicle type can affect delivery speed and therefore delivery duration.

---

## 17. multiple_deliveries

Number of additional deliveries handled by the delivery person.

Example:

```text
0
1
2
3
```

Multiple simultaneous deliveries can increase the total delivery time.

---

## 18. Festival

Indicates whether the delivery occurred during a festival.

Possible values:

```text
Yes
No
```

Festivals may increase order volume and traffic, potentially affecting delivery time.

---

## 19. City

Type of city where the delivery occurred.

Examples:

```text
Urban
Metropolitian
Semi-Urban
```

City type can be associated with differences in traffic, population density, and delivery distance.

---

# Target Variable

The target variable is:

```text
Time_taken(min)
```

The original dataset stores this value in a format such as:

```text
(min) 24
(min) 33
(min) 26
```

Therefore, preprocessing is required to remove the `(min)` text and convert the values into numerical format.

After preprocessing:

```text
(min) 24  -> 24
(min) 33  -> 33
(min) 26  -> 26
```

The resulting numerical variable represents the delivery duration in minutes.

This makes the problem a:

```text
Supervised Regression Problem
```

because the model learns from historical examples where the actual delivery time is known.

---

# Project Workflow

The project follows an end-to-end Data Science and Machine Learning workflow:

```text
Raw Data
   |
   v
Data Inspection
   |
   v
Data Cleaning
   |
   v
Missing Value Handling
   |
   v
Outlier Detection
   |
   v
Exploratory Data Analysis
   |
   v
Feature Engineering
   |
   v
Categorical Encoding
   |
   v
Feature Selection
   |
   v
Train / Test Split
   |
   v
Model Training
   |
   v
Prediction
   |
   v
Model Evaluation
```

---

# Data Preprocessing

Raw datasets often contain inconsistencies, missing values, incorrect data types, and unusual observations.

Therefore, data preprocessing is one of the most important stages of this project.

The preprocessing pipeline includes several steps.

## Cleaning Column Names

Column names are inspected and standardized where necessary to make them easier to work with programmatically.

---

## Cleaning String Values

Several columns contain unnecessary spaces.

For example, a categorical value such as:

```text
motorcycle
```

may appear in the raw dataset with leading or trailing whitespace.

Whitespace is removed to ensure consistent categorical values.

---

## Cleaning the Target Variable

The target column contains:

```text
(min) 24
```

instead of:

```text
24
```

The `(min)` prefix is removed and the resulting values are converted to numeric format.

---

## Missing Value Detection

The dataset is inspected for missing or invalid values.

Examples include:

```text
NaN
None
N/A
unknown
```

These values must be handled before machine learning.

Depending on the variable and the amount of missing data, possible strategies include:

- Removing records
- Replacing values with statistical estimates
- Using the most frequent category
- Applying more advanced imputation techniques

---

# Outlier Detection

Extreme observations can negatively affect machine learning models.

This project uses the Interquartile Range method (IQR) to detect statistical outliers.

The process is:

```text
Q1 = First Quartile
Q3 = Third Quartile

IQR = Q3 - Q1

Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR
```

Observations outside these boundaries can be considered potential outliers.

Outlier analysis is performed carefully because an unusual value is not necessarily an incorrect value.

---

# Exploratory Data Analysis

After cleaning the dataset, Exploratory Data Analysis (EDA) is performed to understand the relationships between variables.

The analysis may include:

- Distribution of delivery times
- Delivery time by traffic density
- Delivery time by weather condition
- Delivery time by vehicle type
- Delivery time by city
- Delivery time by festival status
- Delivery time by number of multiple deliveries
- Delivery time versus delivery-person rating
- Delivery time versus delivery-person age
- Delivery distance analysis
- Correlation analysis

The purpose of EDA is not only visualization, but also understanding which variables are likely to contain useful predictive information.

---

# Feature Engineering

Feature engineering transforms raw information into features that are more useful for machine learning.

## Delivery Distance

Using:

```text
Restaurant Latitude
Restaurant Longitude
Delivery Latitude
Delivery Longitude
```

we can estimate the geographical distance between the restaurant and delivery location.

A distance feature can provide significantly more useful information than four independent coordinate columns.

---

## Order Hour

The `Time_Orderd` column can be converted into an hour value.

Example:

```text
19:45:00 -> 19
08:30:00 -> 8
```

This allows the model to learn differences between different times of day.

---

## Pickup Delay

The difference between:

```text
Time_Order_picked
```

and:

```text
Time_Orderd
```

can be used to calculate the pickup delay.

For example:

```text
Order time: 11:30
Pickup time: 11:45

Pickup delay = 15 minutes
```

---

## Day of Week

The order date can be transformed into the day of the week.

For example:

```text
Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```

This may help identify differences between weekdays and weekends.

---

# Categorical Data

The dataset contains several categorical variables.

Examples:

```text
Weatherconditions
Road_traffic_density
Type_of_order
Type_of_vehicle
Festival
City
```

Machine learning algorithms generally require numerical inputs.

Therefore, categorical variables need to be transformed using techniques such as:

- Label Encoding
- One-Hot Encoding
- Ordinal Encoding

The appropriate encoding method depends on the nature of each variable and the selected model.

---

# Machine Learning

After preprocessing and feature engineering, the prepared dataset can be used to train regression models.

The general training process is:

```text
Clean Dataset
      |
      v
Feature Selection
      |
      v
Feature Engineering
      |
      v
Categorical Encoding
      |
      v
Train / Test Split
      |
      v
Model Training
      |
      v
Prediction
      |
      v
Evaluation
```

Possible regression models include:

## Linear Regression

Provides a simple baseline model and helps establish whether the relationships between features and delivery time can be approximated linearly.

## Decision Tree Regressor

Can model non-linear relationships and interactions between variables.

## Random Forest Regressor

Combines multiple decision trees and can provide strong performance on tabular datasets.

## Gradient Boosting Models

More advanced boosting algorithms can potentially provide improved predictive performance.

The final model should be selected based on validation performance rather than model complexity alone.

---

# Model Evaluation

Because this is a regression problem, classification metrics such as Accuracy are not appropriate.

Instead, regression metrics should be used.

## Mean Absolute Error (MAE)

MAE measures the average absolute difference between predicted and actual delivery times.

For example:

```text
Actual:    30 minutes
Predicted: 34 minutes

Absolute Error = 4 minutes
```

A lower MAE indicates better performance.

---

## Mean Squared Error (MSE)

MSE calculates the average squared prediction error.

Large errors are penalized more heavily than small errors.

---

## Root Mean Squared Error (RMSE)

RMSE is the square root of MSE.

It is useful because the result is expressed in the same unit as the target variable:

```text
minutes
```

For example, an RMSE of:

```text
5.2
```

indicates a prediction error magnitude of several minutes, with larger errors receiving greater weight.

---

## R² Score

R² measures how much of the variance in delivery time is explained by the model.

A higher R² generally indicates that the model explains more of the variation in the target variable.

---

# Technologies Used

The project is implemented using Python and common Data Science libraries.

### Programming Language

- Python

### Data Analysis

- Pandas
- NumPy

### Data Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn

### Development Environment

- Jupyter Notebook
- Git
- GitHub

---



# Installation

Clone the repository:

```bash
git clone https://github.com/your-username/food-delivery-time-prediction.git
```

Move into the project directory:

```bash
cd food-delivery-time-prediction
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate the environment on Windows:

```bash
venv\Scripts\activate
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

---

# Requirements

A typical `requirements.txt` file may contain:

```text
pandas
numpy
matplotlib
seaborn
scikit-learn
jupyter
```

---

# Usage

Place the dataset inside the `data` directory:

```text
data/train.csv
```

Then start Jupyter Notebook:

```bash
jupyter notebook
```

Open the project notebook and run the cells sequentially.

The notebook performs the following operations:

1. Load the dataset.
2. Inspect the dataset.
3. Clean raw values.
4. Handle invalid and missing records.
5. Detect outliers.
6. Perform exploratory data analysis.
7. Engineer useful features.
8. Encode categorical variables.
9. Split the data.
10. Train regression models.
11. Generate predictions.
12. Evaluate model performance.

---

# Expected Outcome

After completing the full workflow, the project should produce:

- A cleaned and structured dataset
- Statistical and visual analysis of the data
- Engineered features such as delivery distance and pickup delay
- Encoded machine learning features
- One or more trained regression models
- Evaluation results using MAE, MSE, RMSE, and R²
- A selected model for delivery-time prediction
- Predictions for unseen delivery records

The final system should be capable of estimating the expected delivery duration for a new order based on its available characteristics.

---

# Example Prediction Workflow

After the model has been trained, a new delivery record can be passed to the model.

For example:

```text
Weather: Sunny
Traffic: High
Vehicle: Motorcycle
City: Urban
Multiple Deliveries: 0
Rating: 4.9
```

The model processes these features and produces an estimated delivery time.

Example:

```text
Predicted Delivery Time: 25 minutes
```

The prediction is an estimate based on patterns learned from historical delivery data.

---

# Why This Project Is Useful

Predicting delivery time can be useful for several real-world applications.

## Food Delivery Platforms

A delivery platform can estimate the expected arrival time before an order is placed.

## Customer Experience

Customers can receive more accurate delivery-time estimates.

## Delivery Management

Companies can identify conditions that cause delivery delays.

## Operational Optimization

Businesses can analyze:

- Traffic impact
- Vehicle performance
- Delivery distance
- Weather effects
- Delivery-person workload
- Festival effects

and use these insights to improve their operations.

---

# Important Considerations

The dataset contains geographical coordinates, timestamps, categorical information, and identifiers.

Not every available column should automatically be used as a machine learning feature.

For example:

```text
ID
```

is primarily an identifier and usually provides no meaningful predictive information.

Similarly, high-cardinality identifiers such as:

```text
Delivery_person_ID
```

should be evaluated carefully to avoid unnecessary complexity or overfitting.

Feature selection should therefore be based on both statistical analysis and domain knowledge.

---

# Limitations

The prediction quality depends on the quality and representativeness of the historical dataset.

Potential limitations include:

- Historical data may not represent current traffic patterns.
- Weather information may be relatively coarse.
- Geographic coordinates may not represent the actual travel route.
- External events may affect delivery time but may not exist in the dataset.
- Delivery-person behavior can vary significantly.
- Restaurant preparation time may not be directly available.
- Real-world traffic conditions can change dynamically.

Therefore, the model should be considered an estimation system rather than an exact delivery-time calculator.

---

# Future Improvements

Several improvements can be added to make the project more advanced.

## 1. Advanced Distance Calculation

Instead of using simple geographical distance, road-network distance could be calculated using mapping services.

## 2. Real-Time Traffic

Real-time traffic information could be integrated into the prediction system.

## 3. Weather APIs

Live weather information could improve predictions.

## 4. Advanced Machine Learning

More advanced models such as:

```text
XGBoost
LightGBM
CatBoost
```

could be evaluated against traditional regression models.

## 5. Hyperparameter Optimization

Techniques such as:

```text
GridSearchCV
RandomizedSearchCV
Optuna
```

could be used to optimize model parameters.

## 6. Model Explainability

Techniques such as SHAP can be used to determine which features have the greatest impact on predictions.

For example, the system could determine whether:

```text
Traffic
Distance
Weather
Vehicle Condition
Multiple Deliveries
```

are the strongest contributors to delivery time.

## 7. Deployment

The trained model could eventually be deployed as an API using technologies such as:

```text
FastAPI
Flask
```

A web application could then send delivery information to the API and receive a predicted delivery time.

---

# Final Project Pipeline

The complete project can be summarized as:

```text
                 RAW DATA
                    |
                    v
             DATA INSPECTION
                    |
                    v
              DATA CLEANING
                    |
                    v
          MISSING VALUE HANDLING
                    |
                    v
            OUTLIER DETECTION
                    |
                    v
                   EDA
                    |
                    v
          FEATURE ENGINEERING
                    |
                    v
          CATEGORICAL ENCODING
                    |
                    v
             FEATURE SELECTION
                    |
                    v
            TRAIN / TEST SPLIT
                    |
                    v
            MODEL TRAINING
                    |
                    v
               PREDICTION
                    |
                    v
              EVALUATION
                    |
                    v
        DELIVERY TIME ESTIMATION
```

---

# Conclusion

This project demonstrates a complete machine learning workflow for predicting food delivery time using real-world tabular data.

The project starts with raw delivery records and progressively transforms them into a clean dataset suitable for machine learning.

The analysis focuses on understanding how factors such as:

- Delivery distance
- Traffic density
- Weather conditions
- Vehicle type
- Vehicle condition
- Delivery-person characteristics
- Multiple deliveries
- City type
- Order time
- Festival conditions

can influence delivery duration.

The final objective is to build a reliable regression model that can estimate delivery time from the characteristics of a new order.

Beyond prediction, the project demonstrates the complete Data Science lifecycle:

```text
Data
  |
  v
Cleaning
  |
  v
Analysis
  |
  v
Feature Engineering
  |
  v
Machine Learning
  |
  v
Evaluation
  |
  v
Prediction
```

This makes the project suitable as a practical Data Science / Machine Learning portfolio project and as a foundation for developing a real-world food delivery prediction system.
