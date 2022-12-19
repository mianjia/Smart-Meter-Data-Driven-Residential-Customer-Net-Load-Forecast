# Smart-Meter-Data-Driven-Residential-Customer-Net-Load-Forecast
## Overview
To develop day-ahead net load predictors that do not need any behind the meter (BTM) sensor data, this project takes disaggregated BTM solar generation and customer consumption traces as well as publicly available meteorological data obtained from NSRDB to train two separate predictors for solar generation and customer consumption respectively. The distinct nature of these two sub-problems are exploited for effective input feature selection and neural network architecture design. The outputs of the two trained predictors are then combined to produce the net load forecast. The prediction results are evaluated by two metrics: MSE and hourly NMAE.
## How to Implement
Before running the code, all aforementioned data should be prepared. To disaggregate net load traces into estimated solar generation and customer consumption traces, please refer to [disaggregation](http://www.ece.sunysb.edu/~yzhao/PZ_SGC22.pdf). To obtain meteorological data, please use API from [NSRDB](https://nsrdb.nrel.gov/).

The information used (data_Ithaca.csv) includes:

1.  Load information:
*   load: ground truth residential customer load
*   dis_load: estimated residential customer load
*   solar: ground truth solar generation
*   unsup_solar: estimated solar generation
*   grid: ground truth net load of residential customer

2.  Time information:
*   timeslot: time slot of the day (15 minutes)
*   weekday: day of the week

3.  Meteorological information:
*   temp: temperature
*   dew: dew point
*   wind: wind speed
*   hum: relative humidity
*   press: air pressure
*   water: precipitable water
*   zenith: zenith angle
*   GHI: global horizontal irradiance
*   cloud: cloud type (categorical)

## Forecasting Procedure

