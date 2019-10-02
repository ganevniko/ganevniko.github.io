---
layout: post
title:      "A LSTM neural network to forecast daily S&P500 prices"
date:       2019-10-02 20:49:19 +0000
permalink:  a_lstm_neural_network_to_forecast_daily_s_and_p500_prices
---


It is well known that the stock market exhibits very high dimensionality due to the almost unlimited number of factors that can affect it which makes it very difficult to predict. Studying how global stock market indexes respond to headlines can provide a major advantage in predicting stock movements and making trade decisions. Naturally, fundamental and technical indicators are not to be neglected and the goal of the project is to combine all of these aspects to achieve a model that thinks as an experienced trader. 

<b><u>The Data Sources</u></b>

The first step is to assemble the data we will use for the model inputs and clean it.

**News Data -** Currently, official data sources to obtain historical financial news are limited. Most sources like NewsApi only allow access to the last few days of data for free and it would cost approximately $1000 to gather all the data necessary for this project. I was able to find a dataset from a Harvard Database providing 16 million financial headlines with timestamps from January 2007 to December 2017.

I will use news NewsApi to collect last 30 days’ worth of news for an additional test dataset.

**Fundamental and Technical Data –** pandas_datareader - Pandas has an extremely useful library for finance. I used the library to be able to pull any stock's live data from multiple sources. For the purpose of this project I chose Yahoo Finance as main source by passing the yahoo argument into pandas_datareader. Once I have obtained Open, Close, High, Low and Volume for the dates I need, all the technical indicators like RSI, MACD and Moving Averages are calculated manually with a few lines of code.

**Correlated Assets -** Correlated assets as ETFs representing the major industries part of the S&P500 are great candidates for significantly useful feature to predict the target. They are unfortunately likely to generate multicollinearity between the features but that will be fixed while performing dimensionality reduction through PCA. In addition to data from the targeted SPY ETF, I have selected the following ten tickers to extract features from:

* **•	XLF** for Financials
* **•	EEM** for Emerging Markets
* **•	XRT** for S&P Retail
* **•	FXI** for China Large Cap
* **•	XHB** for S&P Homebuilders (Tracks real estate)
* **•	TLT** for 20 year Treasury Bond
* **•	USO** for US Oil Fund
* **•	DBC** for Commodity Tracking
* **•	GLD** for Gold
* **•	QQQ** for Nasdaq 100

<b><u>Processing the Data – EDA </u></b>

Every data scientist knows how tedious and time consuming the exploratory data analysis phase of a project can be. For this reason I will only be able to review some milestones of the processing that I had to perform on the data before being able to use it for modelling.

Our initial news data had sixteen million rows timestamped per minute. Using pandas datetime function, I reorganized the news to include all news occurring prior to 9am with previous day news because the market opens at 9.30am and these early morning news can make a significant difference in the sentiment analysis. I also excluded from the news all news occurring during market business hours because I assume those get immediately reflected in the price of the index. Because I am using days as predictors all the news for the same day were concatenated in a large text type string. Most of the difficulty during that process came from managing week end and holidays data because new come out on non-business days as well. I found the “holidays” library very useful with extracting market business days to be able to clean the news data accordingly.<r>
Once this news data reorganized in large daily strings, I processed each daily data with Vader sentiment analysis tool from the NLTK library. 

The correlated assets data mostly needed de-trending in order to be able to achieve good results while modelling. It was mostly achieved through differencing. Below you can see an example of the data before and after the differencing:

![](img/31)

Finally, after calculating technical indicators like Relative strength Index (RSI), MACD and moving averages, the data was scaled using Scikit-Learn MinMaxScaler and dimensionality was reduced using PCA from close to one hundred features to thirty features thus preserving 95% of the data variances. The main reason for performing PCA was to eliminate correlation between features because a lot of the indicators we are using are correlated among each other’s.

<b><u>Modelling</u></b>

**ARIMA:** I first attempted to run an ARIMA model and the result are good but unfortunately not enough to be able to generate profits. Below is a chart of the ARIMA model predictions vs actual price:

![](img/32)

I decided to use the output of this ARIMA model as an input to my LSTM Neural Network model and basically add it as an additional engineered feature to my dataset besides the technical indicators that engineered previously.

**LSTM Neural Network:** The model I used was fairly simple: one layer only to avoid overfitting and RMSE as loss function. Nevertheless, many challenges came with training this model until achieving something that could be used for trading. 

The First one was to choose the sliding window to use for our predictions. Basically I needed to decide what is the best number of previous days to use to predict tomorrows price. I tried values between one and sixty and the best results (lowest RMSE) were achieved for sliding values between five and nine trading days. I decided to go with seven.

The second issue was how many days to train the data on? I had approximately ten years’ worth of data or around 2600 rows but training on the entire data set was resulting in overfitting: I was getting a very low loss on the training set but the results on the testing data were quite poor. To avoid overfitting I had to use **K-Fold Cross validation** by training in increments of sixty days and training on thirty days and looking at the RMSE on the test data. 

By plotting the resulting RMSE values, I obtained the following chart: 

![](img/33)

I first thought that I won’t be able to get much out of it since it is oscillating up and down and there is no trend with a minimum or maximum. But I noticed that between ten and fifteen which corresponds to 600 and 900 days the RMSE remains low and doesn’t increase which lead me to focus on this length of training sets.

 After retraining the model on 750 days I achieved results that seemed good enough to start implementing a back testing strategy and hope t would be profitable.

<b><u>Back-Testing</u></b>

The trading strategy used to back test is very simplistic: we assume the algorithm places a limit order at the predicted prices before the market opens and always sells at market close if filled. In other words, if the open price on a given date is lower than the prediction we buy at open and sell at close. If the open price is higher than the prediction we look at the low for that day, if the low is higher than the prediction the algorithm didn’t trade if the low is lower than the prediction we bought at the predicted price and sold at close. The chart below shows the returns of the model against a buy and hold strategy for October 2018 to September 2019.

![](img/34)

<b><u>Conclusion</u></b>

The Neural Network was able to slightly outperform the market portfolio. Of course he assumed no trading fees here but for an individual investor with small funds buying a few shares a day this model could be implemented on platforms that don’t charge a fee and there is an increasing number of them on the market currently. 





