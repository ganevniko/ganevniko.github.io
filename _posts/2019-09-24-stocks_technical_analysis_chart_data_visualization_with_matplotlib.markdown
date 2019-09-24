---
layout: post
title:      "Stocks Technical Analysis Chart – Data Visualization with Matplotlib"
date:       2019-09-24 16:51:58 -0400
permalink:  stocks_technical_analysis_chart_data_visualization_with_matplotlib
---


In -- this blog I will show you how to build a technical analysis chart from scratch using Matplotlib. The library is widely used for data visualizations but many might be unaware of how powerful it actually is and we will try to build a professionally looking technical analysis chart for stocks that replicates the quaity of charts you might see on some very modern trading apps, maybe they were also built on Matplotlib ?  
The official documentation on Matplotlib can be found here: https://matplotlib.org.


For the purposes of this blog we will use the SP500 ETF as an example to obtain data. If you don’t have the pandas_datareader library installed yet, start by running the pip install pandas_datareader and pip install mpl_finance . The first library will be used to pull financial data from yahoo and the second is what will allows to build candlesticks on Matplotlib. Next, run the following piece of code to import the necessary libraries:

![](img/1.png)

The next step is to pick our beginning and ending dates for the chart and pull the data: 

![](img/2.png)

With the data now available let’s add some columns to plot by calculating some common technical indicators used in technical analysis:

-200 days moving average

-MACD – Moveing average Convergence/ Divergence

-RSI – Relative Strength Index

Please note that the purpose of this blog is not to explain how this indicators are used, we are focusing on the technical aspect of building the chart. The following code will add the MVA7 and MVA200 columns to the pandas data frame:

![](img/3.png)

The following code will add the MACD column to the pandas data frame:

![](img/4.png)

Since the moving averages are calculated based on the available data only, thy will have NaN values for the number of days prior to the first day they can be calculated for. To avoid having missing values while visualizing the data, let’s drop this NaN values before moving forward. 

![](img/5.png)

The next step will be to prepare the data to meet mpl_finance requirement to plot candlesticks. Candlesticks are boxplots: they show the starting value, ending value, max value and min value. Also they will usually be red if the ending value is lower than beginning value for the period and green if the opposite is true. In order to be inputted in mpl_finance, the dates must be converted to numbers and value columns must be organized as tuples with the following piece of code: 

![](img/6.png)
![](img/7.png)

The next step will be to create a figure and the axes we are going to be plotting on.  Note that the following piece of code split the figure in five rows and four columns and we will only be using four rows and four columns in the initial axis. The reason for that is to save space to plot volume later on. 

![](img/8.png)

We are ready to have a first look at our candlestick chart of S&P500 price from January 2016 to October 2019. Using the candlestick_ohlc function from mpl_finance library lets plot our data:

![](img/9a.png)
![](img/9b.png)

The result is very satisfying but we are still far from the professional looking chart we are trying to achieve. Some of the first things coming to mind when looking at this plot are the format of the date, missing grid, missing volume, missing technical indicators, colors could be improved….

Before starting to modify our graph parameters I like to glance at an illustration on the Matplotlib official documentation that shows all the different part we are working with.

![](img/10.png)
Source: https://matplotlib.org/gallery/showcase/anatomy.html

From this point on all the lines of code will be added between the line defining the axes starting with “ax=” and the line used for plotting.  We will personalize all of the components showed on the documentation one by one to achieve an impressive technical chart.


First we need to format the date value on the x axis, they are showing as a type of unix timestamp numbers since we had to convert them to satisfy mpl_finance requirements. The .set_major_formatter() function applied to the axis combined with matplotlib.dates formatter we imported will allows to achieve the desired outcome as follows:

![](img/11.png)

The next point will be to add a grid on our axis with the .grid() function. In this case we are looking for a dotted line for the grid and setting the color of the grid to white since we will be changing the background color of the chart to black.

![](img/12.png)

To prepare for the black backround of the graph we need to change the colors of the spines, labels, title and tick of both axis.

![](img/13.png)
![](img/14.png)
![](img/15.png)


We can now add lines for our moving average MVA200 and also update the figure and axis lines to pass the facecolor parameter to black and lets also change the size to (18,12) in order to make space for more feature we will be adding.
Replace the initial figure and axis ‘ax’ with the following: 

![](img/16.png)

Plotting the moving average in yellow and adding a legend for it:

![](img/17.png)

If we now run the code to visualize the chart this what we should be obtaining: 

![](img/18.png)

Amazing! We have gone a long way from the initial chart to this improved version but there are still a few things to add in order to make it functional for technical analysis. Let’s add volume on the same axis and then MACD on a second axis underneath as well as a title.

The secret to adding the volume on top of the price chart is the shared axis function. This function is the .twinx() and allows to plot two different datasets on the sane x axis. It is creating a replica of the x axis and we need to configure al the settings of the axis as previously. To plot the volume we will use a line and fill between the x axis and the line. When using the .fill_between() function, use the alpha parameter to set up the transparency of the color.. A common issue is that the volume will come to overlap on the chart and hide candlesticks. In order to keep the volume to the bottom of the chart we can increase the max value on the y axis for the volume so all the values appear small.  See example below. 

![](img/19.png)

Similarly we can add a subplot to show the MACD. Please not that when using the .subplot2grid() function Matplotlib is counting from the top left corner as the origin.  An example of placing MACD on top of the chart would be as follows:

![](img/20.png)

Finally I add the Relative Strength Index (RSI) on a subplot at the bottom of the chart, along with the 30 and 70 thresholds used for decision making with RSI, in a similar fashion to what we  did with the MACD to obtain the final chart shown below. 

![](img/21.png)

### **Conclusion:**
In summary we learned how to pull financial data from the internet and use it to build a styled, usable technical analysis looking like the ones you see on trading apps. Since stocks data is updated a few times per second during trading hours, it would be interesting to follow up on this blog post with a second part using the animation function in Matplotlib to make this chart a live updating chart. 













