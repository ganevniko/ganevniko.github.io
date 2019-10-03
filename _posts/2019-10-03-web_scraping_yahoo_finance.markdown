---
layout: post
title:      "Web Scraping Yahoo Finance"
date:       2019-03-27 17:30:28 -0400
permalink:  web_scraping_yahoo_finance
---


It is very likely that every data scientist will need web scraping at some point in their career and it is important to be comfortable with it, regardless how confusing it could seem at first, especially for somebody not familiar with HTML code. The objective of this blog is to use web scraping techniques to scrap data about US stocks from Yahoo Finance and Wikipedia websites. There are currently some great libraries like pandas_datareader or quandl that allow us to collect most of this data very easily with built in functions. But, for the purposes of this blog we will ignore these libraries because our goal is to write from scratch code that will pull targeted financial data from the selected websites and organize it in a Pandas data frame.

The pages we will be scraping information from for the moment are the following:
* [https://finance.yahoo.com/quote/AAPL?p=AAPL&.tsrc=fin-srch](https://finance.yahoo.com/quote/AAPL?p=AAPL&.tsrc=fin-srch)
* [https://finance.yahoo.com/quote/AAPL?p=AAPL&.tsrc=fin-srch](https://finance.yahoo.com/quote/AAPL?p=AAPL&.tsrc=fin-srch) 

In order to parse the HTML page I will be using Beautiful Soup which is a python package for parsing HTML and XML documents. Documentation about the package can be found here: [https://www.crummy.com/software/BeautifulSoup/bs4/doc/](https://www.crummy.com/software/BeautifulSoup/bs4/doc/).

I will also need the Urllib package for working with URLs and accessing the HTML we are going to input into beautiful soup for parsing. We will only use urllib.request. Documentation about this package can be found here : [https://docs.python.org/3/library/urllib.request.html#module-urllib.request](https://docs.python.org/3/library/urllib.request.html#module-urllib.request).

<b><u>Accessing a single data point on the page</u><b>

Once installed if needed, let’s import our libraries: 

![](img/35.png)

The first step will to connect to our URL with urllib.request library to obtain the HTML page we are going to be looking through for our data point.

![](img/36.png)

At this point, the HTML code for our URL is loaded into Python but unfortunately it looks something like that:

![](img/37.png)

As you can see this is unfortunately not something we are going to be able to work with. This is were Beautiful soup comes in to transform this unreadable HTML into something a lot more user friendly. This is also the most difficult part (at least for me): finding the data we need within the HTML code elements. I think the best way to get to the data you are targeting on the page is first to see what type of element it is. For example, in our case the data we are looking for is all in cells of a table. By doing some online research we find that ‘td’ is used to refer to cells of a table in HTML language. Let’s parse the page accessed previously with Beautiful Soup and then fetch all the ‘td’ elements:

![](img/38.png)

This is looking a lot better! We have all the data from the table on out Yahoo Finance table and all we have to do now is grab them and add them to a Pandas data frame. Let’s experiment with the firs two data points: 

![](img/39.png)

It is great to see that our scraping algorithm is working properly and we start perceiving how powerful it could potentially be.  

<b><u>Building a data frame with all the features we want about stocks of our choice from Yahoo Finance</u><b>

The next step would be to create an empty data frame before we start filling it with the data from the web pages we are targeting.  When doing that I will create three lists that will allow us to add more tickers or features. The first list will contain all the tickers (companies) we want to collect data about. The second and third lists will allow us to choose which data points we want from each of the two pages. Let’s create the data frame: 

![](img/40.png)

Once we have the skeleton ready we can start filling it by looping over the tickers, pages and features. The following piece of code is going to go over each feature on each page for each ticker, scrap the value from the HTML page and save it into the df dataframe.

![](img/41.png)

And the pandas data frame we obtain looks like that:

![](img/42.png)

<b><u>Conclusion:</u><b>

We have achieved our goal of collecting data from a multitude of web pages and aggregating it into a pandas data frame. Remember that for each ticker the algorithm has pulled two different Yahoo Finance pages related to that ticker and collected information from them to store in pandas. Here in less than a second we collected data from ten webpages. I tried the experiment with the entire SP500, that is to say one thousand web pages and python was able to build the data frame in around five minutes. The code in this blog is reusable for any URL if you are looking to scrap data contained in table cells. For data in paragraph or other HTML element the code will need to be updated. Please reach out if you believe I can help you scrap a web page you are having difficulty with. 


