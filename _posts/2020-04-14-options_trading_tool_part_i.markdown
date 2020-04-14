---
layout: post
title:      "Options trading tool – PART I"
date:       2020-04-14 19:36:11 -0400
permalink:  options_trading_tool_part_i
---


In this new project we will be looking at way to screen stock and obtain information on option prices with python. This is only a sort introduction to the new project that I will be building over the next few editions of this blog series. The goal is to build a stock scanner, an option pricing tool and web interface for user to  be able to interact with it and make stock trading decisions.

<b><u>The Stock Scanner<u>

The stock scanner will have for purpose to identify tickers that are likely to exhibit sharp movement in price and be good candidates for placing options trades. I will be using pandas_datareader to pull the stock data and then process it with in house function  I will write on python. These functions will be monitoring technical indicators signaling an upcoming move. The indicators we will use are RSI, sharp changes in volume, prices relative to moving averages and others. <br>

The first step will be to select our start and end date to be used in pandas_datareader  as well as a few sample tickers. I will use the date time library to format my dates. Let’s import the necessary tools:

<img/146.png>

And select a few sample tickers, I am aware that I have the SPY twice in this list but this might actually be useful for bug testing purposes of my tool.

<img/147.png>

In order for pandas_datareader to process dates correctly they need to be under the following string format: YYYY-MM-DD. I will use the date to string built in function from the datetime library to achieve that as shown below. Also I will use the time delta function to pick a start date a year in the past. The reason I want my end date to be today is because I want current data and the reason for the start date to be a year prior is because I will be calculating indicators requiring previous data. For example, the two hundred days moving average will require two hundred trading days which is a little over nine months. I rounded it up to a whole year.

<img/148.png>

We are ready to create our data frame and look at some of the stocks data.

<img/150.png>

Everything looks good and we can start building some technical indicators data. Let’s start with the easier ones: the moving averages using python built-in function as shown below:

<img/149.png>

<b><u>Conclusion<u>

In this blog we looked at the first steps of creating an option valuation tool and deploy it to a flask application. There still a lot of work on the tool but over the next weeks I will add publication to these blog series and show a step by step process of how the tool is built. Next blog will look further into the stock scanner before we start looking at option chains of the selected stocks. 


