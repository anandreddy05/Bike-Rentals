# Bike Rentals Forecasting

============================

## Dataset Information

This dataset originates from the Capital Bikeshare system in Washington D.C., covering the years 2011 and 2012. The data has been aggregated at hourly and daily levels, with additional weather and seasonal information extracted from external sources.

### Source:

`Author`: Hadi Fanaee-T (Laboratory of Artificial Intelligence and Decision-Support, University of Porto)

- `Weather Data`: Extracted from freemeteo.com

- `Bike Sharing Data`: Available at Capital Bikeshare System Data

### About the Data

The dataset includes multiple features influencing bike rental demand, such as date, season, weather conditions, and user type (casual vs registered users).

Key Features:

`instant`: Record index

`dteday`: Date

`season`: Season (1 = Spring, 2 = Summer, 3 = Fall, 4 = Winter)

`yr`: Year (0 = 2011, 1 = 2012)

`mnth`: Month (1 to 12)

`hr`: Hour of the day (0 to 23)

`holiday`: Whether the day is a holiday (1 = Yes, 0 = No)

`weekday`: Day of the week

`workingday`: Whether the day is a working day (1 = Yes, 0 = No)

`weathersit`: Weather condition (1 = Clear, 4 = Severe Weather)

`temp`: Normalized temperature (divided by max 41°C)

`atemp`: Normalized perceived temperature (divided by max 50°C)

`hum`: Normalized humidity (divided by max 100%)

`windspeed`: Normalized wind speed (divided by max 67)

`casual`: Number of casual users

`registered`: Number of registered users

`cnt`: Total number of bike rentals (casual + registered users)

## Exploratory Data Analysis (EDA) Summary

## Seasonal Trends

1. Demand for Rental Bikes (y)

- Highest demand is observed from May to October (spring to early fall).
- Possible reasons: Warmer weather, longer daylight hours, and increased outdoor activities.
- Recommendation: Further analyze by day of the week to see if weekends have higher demand.

## Quarterly Demand

- Q3 (July - September) sees the highest demand for rental bikes.
- This aligns with peak summer, vacations, and increased outdoor movement.
- Business Insight: Promotions and marketing should be focused on Q2-Q3.

## AutoCorrelation Analysis (ACF)

- Significant autocorrelation up to lag 50 → Strong influence of past values.
- This means bike rentals are influenced by past trends over roughly 50 time units (days or hours, depending on granularity).
- Implication: Forecasting models should include long-term dependencies.

## Partial AutoCorrelation (PACF)

- Significant correlation up to lag 6 → Short-term dependency (6 days).
- This suggests a weekly pattern where rental trends reset every ~6 days.
- Implication: A 7-day lag feature should be included in the forecasting model.

## Holidays

- Added Holidays as the holidays might affet the bike rentals as people might use more rental bikes at holidays.

## Prophet Model

### Key Insights from Forecasting

- Higher rentals on working days (commuters using bikes for work travel).

- Bad weather conditions (wind, humidity, rain) decrease rentals.

- Higher temperatures encourage bike usage.

- Wind speed has the strongest negative impact (logical, as cycling against strong wind is difficult).

## How to run

Create a Virtual Environment (Recommended)

```bash
python -m venv venv
```

activate the venv

```bash
venv\Scripts\activate
```

Clone the repository

```bash
git clone https://github.com/anandreddy05/Bike-Rentals.git
```

Navigate to the Project Directory

```bash
cd Bike_Rentals
```

Install Dependencies

```bash
pip install -r requirements.txt
```

## Future Improvements

Feature Engineering: Add external factors like traffic data.

Deep Learning Models: Compare Prophet results with LSTMs.

Hyperparameter Tuning: Optimize changepoint and seasonal settings.

Deployment: Convert the model into an interactive web app.

## Conclusion

This project provides valuable insights into bike rental trends using Prophet time series forecasting. By incorporating seasonal, weather, and autocorrelation patterns, we can optimize bike availability and improve user experience.
