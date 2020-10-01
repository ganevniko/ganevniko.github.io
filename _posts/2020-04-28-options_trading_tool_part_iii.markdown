---
layout: post
title:      "Options trading tool – PART III"
date:       2020-04-28 19:25:34 -0400
permalink:  options_trading_tool_part_iii
---


This is the third part of our stock scanner project. In this project we are looking at ways to screen stocks and obtain information on option prices with python. In this blog we will use the tickers and data assembly techniques learned in parts one and two to create a data frame with all the technical indicators we are targeting. 

Lets star by creating out list of tickers as preciously. Below, I have also put together a list of tickers to remove. The reason I am removing these tickers is because pandas_datareader is unable to retrieve information about them which could be caused by several reasons that I will not investigate for the moment. We will still be using close to five hundred tickers which is probably way more that we could invest in.

![](img/157.png)

The next step is to use pandas_datareader to assemble the data frame we will use for analysis and decision making. This process was explained in detail in part one and as a reminder, the code is below.

![](img/158.png)

Just as in part one, lets create our moving averages. Note that in the moving averages I only need the most recent that and for this reason I only keep the last seven days of data.

![](img/159.png)

The next piece of code I am going to show is quite large. The goal here is to create a dictionary of dictionaries. The keys in our higher level dictionary are the tickers, then for each ticker we are adding a second dictionary containing the values for each one of the technical indicators we want to monitor. <br>

The logic here is to iterate through each ticker of our ticker list and calculate every single one of the technical indicators we will be looking for and saving it as value in a dictionary for the ticker itself as a key. Some indicators are:<br>
* Price
* 200 days moving average
* 50 days Moving average
* 7 days moving average
* 30 days average volume
* 10 days average volume
* Relative Strength Index (RSI)

![](img/160.png)

For the Relative Strength index you will notice that I am calling a function. I do not know of any library or package offering to calculate RSI for you. I have written my own function and back tested it. I will explain how this function works and show the code in a future publication. It can also be found in my SP500 stock prediction project on my github. 

<u><b>Conclusion

We have used the techniques shown in the previous parts of this blog series to assemble useful daily data about or tickers. This data will now be used to select which tickers we will be looking at when we want to place option trades. In order to decide how to rank the tickers from most attractive to least attractive I will be implementing a simple points system in the next publication if this blog series. 

