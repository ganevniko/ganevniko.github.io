---
layout: post
title:      "Options trading tool – PART II"
date:       2020-04-21 22:55:11 +0000
permalink:  options_trading_tool_part_ii
---


This is the second part of our stock scanner project. In this we are looking at way to screen stocks and obtain information on option prices with python. In this publication I will use the stock data and moving averages we gathered in the last blog and add a few features that will allow us to screen for tickers.

<b><u>Gathering a list of tickers</u>

The first task would be to gather a list of tickers to work with. We could take several approaches to achieve this, like scrapping them directly from webpages such as yahoo finance, but the one I will suggest here is most likely the easiest one. The yahoo_fin library will allow us to put together a list of over four thousand stocks in a few seconds. I will then save this list to a CSV file to allow my stock scanner to read from it when we run it on a daily basis. Let’s start by installing the library.

![](img/151)

Next we import stock_info from the library we just installed along with the requests library because yahoo_fin needs requests to work. 

![](img/152)

We are now ready to generate a list of stocks. Below is screenshot of the documentation of yahoo_fin with the methods we will use. 

![](img/153)

This methods simply returns a list with tickers in them. I will aggregate all these list except the with crypto tickers because we are looking to trade options and crypto stock do not offer options (for the moment).

![](img/154)

