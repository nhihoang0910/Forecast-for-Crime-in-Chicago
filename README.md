# Forecast for Crime Rate in Chicago
## Table of Contents
1. [Project Background](#project-background)
2. [Approach](#approach)
    - [Statistical Tests Used](#statistical-tests-used)
    - [Library Used](#library-used)
3. [Main Findings](#main-findings)
4. [Insight Deep Dive](#insight-deep-dive)
    - [Trend and Seasonality](#1-trend-and-seasonality)
    - [Confidence Intervals](#2-confidence-intervals)
    - [Model Accuracy](#3-model-accuracy)

# Project Background
The project aims to build a prediction model to forecast the crime counts in the City of Chicago in the next 5 years using ARIMA (Autoregressive Integrated Moving Average) Time Series approach. This dataset is extracted from the Chicago Police Department's CLEAR (Citizen Law Enforcement Analysis and Reporting) system. Find more details [HERE](https://catalog.data.gov/dataset/crimes-one-year-prior-to-present)

# Approach
- The data that is used to build the forecast didn't include records in 2024 as the year hasn't ended.
- Prior to training the model, I used the following statistical tests to ensure the validity and reliability of the model:
    - ADF (Augmented Dickey-Fuller) Test: Used to check the stationarity of the time series data. This test is crucial for determining whether differencing is needed to stabilize the mean of the series.
    - ACF (Autocorrelation Function) and PACF (Partial Autocorrelation Function): Utilized to identify the appropriate lag values for the ARIMA model's autoregressive (p) and moving average (q) parameters.
    - Seasonal Decomposition: Applied to identify and isolate seasonality in the time series data, guiding the use of SARIMA over ARIMA for seasonal patterns
- Library used for ARIMA and SARIMA Model: statsmodels.tsa.statespace.sarimax
  
# Main Findings
![image](https://github.com/user-attachments/assets/556d76ce-fdff-43dc-a04f-0a673c87917b)
This graph illustrates a 5-year forecast of crime counts in the City of Chicago using the SARIMA Model with parameters (0,1,1)(1,1,1,12), which accounts for both trend differencing (d=1) and seasonal differencing (D=12) with a 12-month seasonal cycle. 

# Insight deep dive
### 1. Trend and Seasonality: The model captures the downward trend in crime counts observed in the historical data.
The projected crime counts for the next five years (2024–2028) show continued seasonal variations, indicating that certain times of the year may consistently experience higher or lower crime rates.
### 2. Confidence Intervals: The shaded gray area represents the 95% confidence interval of the forecast.
This range highlights the uncertainty in predictions, which increases over time, reflecting the inherent challenges in long-term forecasting.
### 3. Model Accuracy: This SARIMA Model (0,1,1)(1,1,1,12) is the most accurate model after comparing various non-seasonal and seasonal ARIMA models with different parameters. My evaluation was based on the following metrics:
   - Mean Squared Error (MSE): Used to measure the average squared difference between observed and predicted values.
   - Mean Absolute Error (MAE): Evaluated the average magnitude of errors in predictions.
   - Akaike Information Criterion (AIC) and Bayesian Information Criterion (BIC): Compared models based on their goodness-of-fit while penalizing for complexity.
