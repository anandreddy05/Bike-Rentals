# Bike Rentals Forecasting

## About The Data

- instant: record index
- dteday : date
- season : season (1:springer, 2:summer, 3:fall, 4:winter)
- yr : year (0: 2011, 1:2012)
- mnth : month ( 1 to 12)
- hr : hour (0 to 23)
- holiday : weather day is holiday or not
- (extracted from <http://dchr.dc.gov/page/holiday-schedule/>)
- weekday : day of the week
- workingday : if day is neither weekend nor holiday is 1, otherwise is 0.

## weathersit

- 1: Clear, Few clouds, Partly cloudy, Partly cloudy
- 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
- 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
- 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
- temp : Normalized temperature in Celsius. The values are divided to 41 (max)
- atemp: Normalized feeling temperature in Celsius. The values are divided to 50 (max)
- hum: Normalized humidity. The values are divided to 100 (max)
- windspeed: Normalized wind speed. The values are divided to 67 (max)
- casual: count of casual users
- registered: count of registered users
- cnt: count of total rental bikes including both casual and registered

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
