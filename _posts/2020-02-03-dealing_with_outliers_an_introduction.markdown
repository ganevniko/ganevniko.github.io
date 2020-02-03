---
layout: post
title:      "Dealing with outliers: an introduction"
date:       2020-02-03 23:46:39 +0000
permalink:  dealing_with_outliers_an_introduction
---


![](img/101.png)

Outliers are observations looking abnormal regarding the whole feature space or placed at a significant distance from the other data points. They can be mistaken data resulting from errors in records or wrong calculations. They can also be the result of an exception in the dataset not resulting from any kind of mistake. For example, a twelve feet tall person is probably a mistake, but a seven feet five person can easily be an exception, it is rare but not impossible or unheard of. In a univariate world identifying outliers can be handled with a visualization. Box plot and scatter plots tend to be my go to visualizations before I decide if I want to screen the data for anomalies any further. For example, consider the box plot below regardless of what data precisely we are working with:

![](img/102.png)

The red dots are clearly outliers and can easily be identified by visualizing. These outliers will most likely be simply dropped during the data cleaning process. Let’s assume that you have now cleaned your data and all the points that were clearly outliers for one reason or another were dealt with by dropping or adjusting them. Are you now outlier free? Unfortunately, when working with real world data you will most of the time have more than one feature and outliers start being more difficult to spot in that environment. For example, consider the US population, a three-year-old is not an outlier and a salary of one hundred and fifty thousand is not an outlier either but a three-year-old earning one hundred and fifty thousand dollars deserves some looking into. The more features you add the more complicated it becomes to spot the outliers. 

One approach that I like to consider to when I have reason to think that my data is affected by outliers in a multivariate space is Isolation forest. This is an unsupervised learning algorithm that isolates anomalies. Instead of trying to find the trend and exclude the data points that don’t follow it, this algorithm targets finding the data points that are different right away and it is very successful in high dimensional datasets. Below is a piece of code to implement an isolation forest algorithm in Scikit-learn.  

![](img/102.png)

<b><u>Conclusion:</u></b>

There are many steps to be taken before being able to use a dataset for machine learning and modeling purposes. Finding anomalies and dealing with outliers is an important step of the process in order to assure the quality of the data used for training models. In this blog we only scratched the surface about the process of identifying and eliminating outliers. Even if visualization can help us identify many irregular points, this process becomes more complicated when working with highly dimensional spaces and some algorithms like the isolation forest algorithm can be necessary to clean the data. In a future post, I hope to be able to review some of the many other algorithms used to identify outliers. 
