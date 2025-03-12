# Bike Rentals Forecasting

============================

## DataSet

- Hadi Fanaee-T
- Laboratory of Artificial Intelligence and Decision - Support (LIAAD), University of Porto
- INESC Porto, Campus da FEUP
- Rua Dr. Roberto Frias, 378
- 4200 - 465 Porto, Portugal
===============================

Bike-sharing rental process is highly correlated to the environmental and seasonal settings. For instance, weather conditions,
precipitation, day of week, season, hour of the day, etc. can affect the rental behaviors. The core data set is related to  
the two-year historical log corresponding to years 2011 and 2012 from Capital Bikeshare system, Washington D.C., USA which is 
publicly available in <http://capitalbikeshare.com/system-data/>. We aggregated the data on two hourly and daily basis and then extracted and added the corresponding weather and seasonal information. Weather information are extracted from <http://www.freemeteo.com/>

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

## Holidays

- Added Holidays as the holidays might affet the bike rentals as people might use more rental bikes at holidays.

## Prophet Model

### Key Takeaways

- People rent more bikes on working days.
- Bad weather (wind, humidity, rain) decreases rentals.
- Higher temperatures encourage more bike usage.
- Wind speed has the strongest negative effect (makes sense, as cycling in strong wind is difficult).
