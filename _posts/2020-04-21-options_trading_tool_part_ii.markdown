---
layout: post
title:      "Options trading tool – PART II"
date:       2020-04-21 18:55:12 -0400
permalink:  options_trading_tool_part_ii
---

This is the second part of our stock scanner project. In this project we are looking at ways to screen stocks and obtain information on option prices with python. In this publication I will focus on building a list of tickers that we will be working with. Once we have this list we can start using pandas_datareader as shown in the previous blog to build more technical indicators for our stock scanner. 

<b><u>Gathering a list of tickers</u>

The first task would be to gather a list of tickers to work with. We could take several approaches to achieve this, like scrapping them directly from webpages such as yahoo finance, but the one I will suggest here is most likely the easiest one. The yahoo_fin library will allow us to put together a list of over four thousand stocks in a few seconds. I will then save this list to a CSV file to allow my stock scanner to read from it when we run it on a daily basis. Let’s start by installing the library.

![](img/151.png)

Next we import the stock_info function from the library we just installed along with the request_html library because yahoo_fin needs requests to work. 

![](img/152.png)

We are now ready to generate a list of stocks. Below is a screenshot of the documentation of yahoo_fin with the methods we will use. 

![](img/153.png)

These methods simply return a list with tickers in them. I will aggregate all these lists except the crypto tickers because we are looking to trade options and crypto stocks do not offer options (for the moment).

![](img/154.png)

The next step is to save them to a CSV file because we do not want to pull all this data from the internet every time we run the scanner. The tool is already likely to be running pretty slow, which is not an issue since we only need to use it once a day, but we still want to minimize the data we are pulling from online libraries. Below is code I found on stackoverflow [here]( https://stackoverflow.com/questions/14037540/writing-a-python-list-of-lists-to-a-csv-file) to save your list to a csv library. Note that, the code to create the list will only be used once. As soon as the csv file is created in your app directory you can archive this code.

![](img/155.png)

We now only need a piece of code to be able to pull this list of tickers every time we need to run the scanner. We will use the CSV library again since we only have four thousand elements. Note that if you were to do this with tens or hundreds of thousand pandas would be more efficient.

![](img/156.png)

<b><u>Conclusion</u>

Today we did not build any features but the step accomplished gathered us the only database we are going to utilize for this project and it is so light that we only saved it in a CSV file, no SQL or other needed here. In the next publication I will focus on building additional indicators. Most of them will be simple calculations at the exception of Relative Strength Index (RSI) that would require a function. 


	

