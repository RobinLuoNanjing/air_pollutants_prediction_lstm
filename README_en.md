# air_pollutants_prediction_lstm
This project is for predicting the future condition of the air pollutants in London. There are 5 monitoring stations data will be used in this project, including Harlington, North Kensington, Marylebone, Bloomsbury and Eltham. The data sources from openair, which is an opensource package. The date of data ranges from 2018 to 2019. Air pollutants include NOX, NO2, NO, O3, PM2.5, wind direction, wind speed and the temperature of the air. Since the code is not the object-oriented style, it might be messy but each file can be operated independently.


![image](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/MD_pic/location.jpg)


# Environment
- google colab (Recommand)

or

- pytorch
- numpy
- matplotlib
- seaborn

# Models
Before implementing these models, you need to [preprocess data](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/data_process.ipynb) and understand it.

- lstm (single variable)
- lstm (1 site, 8 variables)
- lstm (5 sites, 40 variables)
- BiLSTM 
- [ConvLSTM](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/convlstm_multivar_sites.ipynb)
- LSTM + Attention
- LightGBM
- ARIMA

> note: Except for BiLSTM, all models use 2 fully-connected layers

# Introduction

## Dataset split
80% training dataset， 10% validation dataset，10% testing dataset。

## Evaluation metrics
There are two methods to evaluate the model. First, it will use 10% testing data to predict the future for 1 hour. It is worth noting that the predicted value will not be inserted into the time window. We only use this method to find the model which is possible to predict a longer period. After that, it will use this model to predict the future 96 hours. Every time predicting one value, this value will be inserted into the next time window. This will cause more offset when you want to predict a long period value in the future.


![image](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/MD_pic/time_window.jpg)

## Result
Here is the result for predicting the NOX value in future 96 hours in Bloomsbury, London

![image](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/MD_pic/results_nox.png)








































### Ackowledgement
- [Openair](https://davidcarslaw.github.io/openair/)
- [ndrplz](https://github.com/ndrplz/ConvLSTM_pytorch)

