---
layout: post
title:      "Basics of feature engineering"
date:       2019-10-27 22:18:10 +0000
permalink:  basics_of_feature_engineering
---


In order to be able to build any kind of predictive model, we need training data and features. Unfortunately, in the real world this data does not come in a format ready to be used by machine learning algorithms. Getting the data ready for modeling is actually the most time consuming task and according to several surveys it takes around sixty percent of the time of the data scientist. Preparing and formatting the input data carefully is crucial to achieving reliable models and in this blog I review a few of the most popular and important feature engineering techniques. 

<b><u>Handling missing values</u><b>

When getting a dataset ready to be run through Machine Learning models, the first thing we would usually do is check for missing value and decide on how to approach them. The reason for the missing values might be human errors, interruptions in the data flow, privacy concerns, and so on. Whatever is the reason, missing values affect the performance of the machine learning models and most of the algorithms don’t accept training data containing missing values. 

<b>          Dropping<b>

One approach to dealing with the issue of missing values is to drop the rows containing this values. This approach could be acceptable in some circumstances and has its advantages when applicable. Dropping missing values allows the data scientist to avoid introducing incorrect data points into the data set and induce poor modelling results. 


<b>          Replacing<b>

When the dataset doesn’t have enough data points to allows to afford dropping entire rows because of a missing value in one of the columns we need to use our own judgement to decide how to approach the issue. There is no general rule of thumb, each dataset is unique.<br>
When dealing with numerical features, replacing the missing data points with the mean is a common solution but it can’t be applied in any situation. For example imagine we are working on estimating the price of a house and we have missing values in the number of bedrooms column, it will probably be acceptable to use the average of the number of rooms and round up to closest integer. On the other hand if we have missing value in the size of the house expressed in square feet using the mean right away will most likely not be a very efficient approach. We could for example take the mean square foot size of houses with the same number of bedrooms and get more reliable values.<br>
When dealing with categorical data we can replace missing points with the value that would be the more neutral and generate the less bias in our model results or we could for example create a whole new category for example “other”.


<b><u>Dealing with outliers</u><b>

Outliers are data points that are way too high or too low, in any case far from all the other data points and not representative of the group. Leaving outliers as they are when running ML models on the data might impact the results of the model and changing or dropping this values is an important step in preparing your data for modeling. In order to be able to make any decisions concerning outliers, we first need to identify these data points and the best way to do that is a visualization. My preferred visualizations to spot outliers are box plots. 

![](img/51.png)

For example the box plot above shows a few outliers. First we can notice that we have a flat line for eleven bedrooms which indicates that there are very few instances, perhaps only one. Also we see that for houses with one, two and six bedrooms we have some very expensive properties that seem to have been priced far above similar properties, and we might need to have a closer look at these datapoints to decide if we need to change any of the values. Once identified, the decision to drop or replace and which replacement values to use is discretionary just as with the missing values. 

<b><u>Binning</u><b>

Binning or discretization is the process of transforming numerical variables into categorical counterparts. An example is to bin values for Age into categories such as 20-39, 40-59, and 60-79, salaries into categories such as $0-$50k, $50k-$100k,$100k+…Binning can be very efficient against overfitting and improve model performance but on the other hand every time we bin values together we lose some information. It is up to the data scientist to find the right bins to achieve the best compromise between performance and overfitting. See below an example of binning. 


![](img/52.png)

<b><u>Log Transformation</u><b>

Logarithm transformation is one of the most commonly used mathematical transformations in feature engineering.<br>
          -Log Transformation deals with outliers and squeezes values in a smaller range.<br>
          -Most models require normally distributed data to achieve optimal performance while most real world datasets exhibit at least some skewness. Log transformation helps with normalizing the data and improves model performance.<br>

Note that the data used for log transformation must be positive and also if you want the resulting values to be all positive you can add one to each value after transformation. 



<b><u>One Hot encoding</u><b>

One hot encoding is the main encoding method in ML, it creates a new feature for each value of the encoded feature and assigns a binary outcome (zero or one) to it. As shown below, the result is that categorical data which is hard to process for most machine learning models is converted to numerical values that can be fed into the models. 

![](img/53.png)

Please note that one of the two columns (male or female) will be dropped before modeling because if the person is not male then she will be female by default and a second column is not needed.


<b><u>Scaling</u><b>

In most cases, the separate numerical features of a dataset do not have a similar range of values. For example if you have the number of bedrooms next to the dollar price of a house you will be dealing with values between zero and ten on one side and hundreds of thousands on the other. This can be very confusing for the ML models trying to compare the columns. For instance, the algorithms based on distance calculations such as k-NN or k-Means  will be the most affected by unscaled data. How do we address the issue? Standardization and Normalization are the most popular and efficient techniques. 



<b>          Normalization<b>

Normalization scales the values in a range of zero to one without affecting the distribution. Please note that you have to deal with outliers before normalizing because the effect of outliers tends to increase with normalization.

![](img/54.png)

<b>          Standardization<b>

Standardization scales the values while taking into account standard deviation. If the standard deviation of features is different, their range also would differ from each other. This reduces the effect of the outliers in the features.
In the following formula of standardization, the mean is shown as μ and the standard deviation is shown as σ.

![](img/55.png)

<b><u>Conclusion</u><b>

In this blog we reviewed the most common and popular feature engineering techniques. As a data scientist these techniques are the most common as well as the most complicated and time consuming part of your job, and the decisions made by the data scientist when feature engineering  are crucial to building well-performing machine learning models. In a future blog, I will go over feature engineering techniques specific to time series data as they tend to be more challenging than regular datasets.  
