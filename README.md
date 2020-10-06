### English version README can be seen here [English version](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/README_en.md)

# air_pollutants_prediction_lstm
这个项目是用于预测伦敦空气质量的状况。其中有五个监测站的数据被选用。这五个监测站分别是:Harlington, North Kensington, Marylebone, Bloomsbury and Eltham. 该数据来源为openair开源库。数据的时间跨度为2018-2019。数据的属性有:NOX, NO2, NO, O3, PM2.5, 风速, 风向和空气温度。因为是用于水毕业的论文，所以整个实验并没有采用面向对象的方式进行封装，所以比较杂乱，见谅。但这样也有好处，就是任何单独的一个Jupter notebook文件
都可以独立的运行实验，并且完成实验的结果。

![image](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/MD_pic/location.jpg)


# 运行环境
- google colab (建议)

or

- pytorch
- numpy
- matplotlib
- seaborn

# 使用算法
在使用算法之前，先要对数据进行[预处理](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/data_process.ipynb)并且理解他们。


- [lstm (单变量)](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/lstm_singvar.ipynb)
- [lstm (单站点, 多变量, 共8变量)](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/lstm_multivar.ipynb)
- [lstm (多站点, 多变量, 共40变量)](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/lstm_multivar_sites.ipynb)
- [BiLSTM](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/Bilstm_multivar.ipynb)
- [ConvLSTM](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/convlstm_multivar_sites.ipynb)
- [LSTM + Attention](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/lstmWithAttention_multivar_sites.ipynb)
- [LightGBM](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/lightGBM_multivar_single_sites.ipynb)
- [ARIMA](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/ARIMA.ipynb)

> 注意: 除了BiLSTM以外，其余算法全都采用双层的全连接层。


# 介绍

## 数据集划分
80% 训练集， 10% 验证集，10%测试集。

## 评估方法
注意！该实验的评估方法有两种。一种是用10%的测试集去评测。这意味着模型只需要预测未来1小时的情况。然后预测10%个相应的1小时。预测出来的值是不会重新放回time window里的。
另外一种，就是用上面筛选出来的模型去预测未来96小时的情况。每预测1小时，预测出来的新的值，将会塞回时间窗口。所以这个过程，偏移将会越来越大。

![image](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/MD_pic/time_window.jpg)

## 结果
下面是预测Bloomsbury未来96小时的NOX含量的结果
![image](https://github.com/RobinLuoNanjing/air_pollutants_prediction_lstm/blob/master/MD_pic/results_nox.png)








































### 致谢
- [Openair](https://davidcarslaw.github.io/openair/)
- [ndrplz](https://github.com/ndrplz/ConvLSTM_pytorch)

