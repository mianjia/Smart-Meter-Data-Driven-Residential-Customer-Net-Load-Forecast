# Smart-Meter-Data-Driven-Residential-Customer-Net-Load-Forecast
## Overview
To develop day-ahead net load predictors that do not need any behind the meter (BTM) sensor data, this project takes disaggregated BTM solar generation and customer consumption traces as well as publicly available meteorological data obtained from NSRDB to train two separate predictors for solar generation and customer consumption respectively. The distinct nature of these two sub-problems are exploited for effective input feature selection and neural network architecture design. The outputs of the two trained predictors are then combined to produce the net load forecast. The prediction results are evaluated by two metrics: MSE and hourly NMAE.
## How to Implement
Before running the code, all aforementioned data should be prepared. To disaggregate net load traces into estimated solar generation and customer consumption traces, please refer to [disaggregation](http://www.ece.sunysb.edu/~yzhao/PZ_SGC22.pdf). To obtain meteorological data, please use API from [NSRDB](https://nsrdb.nrel.gov/).

The Ithaca dataset (data_Ithaca.csv) contains:

1.  Load information:
*   ground truth residential customer load
*   estimated residential customer load
*   ground truth solar generation
*   estimated solar generation
