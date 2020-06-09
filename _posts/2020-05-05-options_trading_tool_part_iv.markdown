---
layout: post
title:      "Options trading tool – PART IV"
date:       2020-05-05 23:23:10 +0000
permalink:  options_trading_tool_part_iv
---

This is part four of our options scanner project. In this project we are looking at ways to screen stocks and obtain information on option prices with python. In this blog we will use the data we collected previously and create with a table that will be served by an HTML page. The HTML page will later put and an AWS S3 bucket to make our results available to the public on a website. 

The last step in the previous blog was to iterate through each ticker of our ticker list and calculate every single one of the technical indicators we will be looking for and saving it as value in a dictionary for the ticker itself as a key. We are now going to implement a point system for each one of the technical indicators we calculated previously. I won’t explain detail the points choices from a financial stand point because this is not the purpose of the blog but I will show all the code. For example a ticket that has an RSI over 65 or below 35 gets two points, but them we give an extra point if the RSI is actually over 85 or below 20. Below is the code for all the points I am using so far:

![](img/161.png)

I will be adding additional points and modifying the way I point different indicators. In this blog I focus on the technical aspect, how you chose to filter the stocks is a personal choice since I am not trying to give any kind of financial advice here or pretend that my point system will deliver any kind of returns. In any case what I want to achieve is a pandas data frame like this one: 

![](img/162.png)

All I did there is to place the data and points calculated previously in a data frame and sort the data frame by points, then I took the fifteen stock with the highest number of points. The code to build this data frame is below:

![](img/163.png)

I am now going to transpose the dataframe and save it. The only reason I transpose it is because my focus is on the tickers and I would rather have them as columns rather than rows.

![](img/164.png)

Now all we need to do is to create a short javascript to displaythe resulting data frame in an HTML page regardless of the number of rows or columns we decide to format it as. My javascript skills are very limited but the script should look something like that:

![](img/165.png)

<b><u>Conclusion</b></u>
  
In today’s blog we processed all the data accumulated previously and implemented a point system based on technical indicators to screen the tickers and select the ones we want to focus on. We even created an html page showing the table with the winning tickers. We can now start looking at options on these tickers. 





