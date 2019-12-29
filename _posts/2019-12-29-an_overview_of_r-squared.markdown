---
layout: post
title:      "An overview of  R-Squared"
date:       2019-12-29 12:37:54 -0500
permalink:  an_overview_of_r-squared
---


This blog is meant to give a basic understanding of how R Squared is calculated and how to interpret it. The question that R squared helps us answer is why a given regression line is better than another possible fitting line.  For example. Look at the example below, which of the below lines will give us the best predictions ?

![](img/85.png)

R-squared is a metric of correlation. Correlation tells us how strongly two variables are related to each other and it is bounded by -1 and 1. A correlation closer to one means that the two variables behave in a similar way. For example temperature and number of people on the beach, the highest the temperature the more people we will have on the beach. On the other hand a correlation closer to minus one would mean that the two variables move in opposite directions. For example, millimeters of rain on a given day and number of people on the beach. And finally, if correlation is close to zero we assume that the two variables move independently of each other. For example, probably tax rates and number of people on the beach. Now that we have an understanding of correlation we can move on to R-squared.  

First let’s look at the formula:

![](img/86.png)

R-square value gives the measure of how much variance is explained by the model. A regression model fits the data well if the differences between the observations and the predicted values are small. The image below shows this difference.

![](img/87.png)

Higher values of R squared would mean that the dots are closer to the regression line while lower values indicate that the dots are further away from the line and our regression model is less reliable. Usually the closer R squared is to one the better our model is performing. Nevertheless, we need to watch out for over-fitting and a model with an R-Squared of one or very close to one is likely overfitting the training data. As a rule of thumb, if your model returns an R-Squared of more than 0.85 I would recommend to use cross validation in order to make sure the model is not overfitting. There are also further measures of R-Squared as Adjusted R-Squared and Predicted R-Squared, these measures are useful in avoiding overfitting and I will discuss them in more details in a future post. 
