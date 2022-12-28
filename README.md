# Smart-Meter-Data-Driven-Residential-Customer-Net-Load-Forecast
## Overview
To develop day-ahead net load predictors that do not need any behind the meter (BTM) sensor data, this project takes disaggregated BTM solar generation and customer consumption traces as well as publicly available meteorological data obtained from NSRDB to train two separate predictors for solar generation and customer consumption respectively. The distinct nature of these two sub-problems are exploited for effective input feature selection and neural network architecture design. The outputs of the two trained predictors are then combined to produce the net load forecast. The prediction results are evaluated by two metrics: MSE and hourly NMAE.
## How to Implement
Before running the code, all aforementioned data should be prepared. To disaggregate net load traces into estimated solar generation and customer consumption traces, please refer to Github site for BTM solar disaggregation at https://github.com/kkkapu/Solar_Disaggregation. To obtain meteorological data, please use the API from [NSRDB](https://nsrdb.nrel.gov/data-viewer).

The information used (cf.sample_dataset.csv) includes:

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
1.  Run Solar_Forecasting.ipynb to train predictor for aggregate level solar generation forecasting. 
2.  Run Load_Forecasting.ipynb to train two different predictors (LSTM & FCNN) for aggregate level residential customer consumption forecasting. 
3.  Run Clustering.ipynb to perform hierarchical clustering given a relatively larger group of residential customers. Customer indices of all the clusters     will be obtained through this step. Each cluster can then be treated as one aggregate customer, where the above two steps can be performed.

## Evaluation
Run Evaluation.ipynb to calculate two metrics, Mean Squared Error (MSE) and hourly Normalized Mean Absolute Error (NMAE).
In order to evaluate net load forecasting accuracy, net_load = prediction_load - prediction_solar needs to be computed first.
