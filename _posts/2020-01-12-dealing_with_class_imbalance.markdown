---
layout: post
title:      "Dealing with Class Imbalance"
date:       2020-01-13 02:24:59 +0000
permalink:  dealing_with_class_imbalance
---


You will rarely run into a balanced dataset when working with real life data. Unfortunately most machine learning models for example regressions or random forests from Sckit-Learn won’t return reliable results when the training data is highly imbalanced. For example, consider a  training dataset of patients being screens for cancer. This dataset will most likely only present a small number of positive cases for example 1%. That means that a model that classifies every single case as healthy will be right 99% of the time be it will also be completely useless. In order to be able to build a reliable model we will then need to first address the imbalance. 

<b><u>Random under-sampling and oversampling</u></b>

These two techniques s their name indicates consist of taking a repeated number of the minority class or the ignore some datapoints in the majority class when training models. Both have their advantages and disadvantages that need to be considered careful if using one of these ways to address data imbalance issues. 

An advantage random under-sampling is the smaller resulting dataset and subsequent faster processing. Unfortunately, it comes at the cost of information loss or variance loss as well as the potential risk of biased datasets. 

On the other hand when using random oversampling we avoid the danger of information loss and have a larger dataset to work with but might generate overfitting because datapoints repeat themselves and we are also running the risk over overfitting.

<b><u>Cluster-based oversampling</u></b>

In this technique, we use K-means or other clustering algorithm which is independently applied to each class. The K-means algorithm is used to detect the clusters in our data set, for example for the major class there might two classes and seven for the minor. Then we oversample objects inside each class so we have balanced data inside each class. Finally we oversample the smaller class to the bigger class. This method helps to solve the misbalancing in general as well as the imbalance inside each class. However overfitting as well as high computational cost are still present.

<b><u>SMOTE – Synthetic Minority Oversampling </u></b>

In SMOTE we take a subset of data from the smaller class and we create new synthetic samples which we add to the dataset. We take a random instance of a minor class and we find three nearest neighbors using for example distance as a metric. Then we randomly chose one of these neighbors, we take a distance vector, we multiply it by a factor and we add it to the initial datapoint and this is how we obtain our new sample for this class. We repeat this process as many times as needed to remedy data imbalance. The risk to create class overlapping and increase noise by creating data points that are closer to the major class. 

SMOTE is usually my go to method for resolving class imbalances and even if the way it works might take some time to understand, using Scikit-Learn SMOTE algorithm to resolve dataset imbalance is very straight forward as showed in the code below.

![](img/93.png)

As shown by the output, the code transformed a dataset of 87% to 13% to a 50/50 distribution of the classes. 

<b><u>Conclusion:</u></b>

In conclusion there are many ways to address dataset imbalances, some simpler than others. I personally tend to prefer SMOTE if dealing with a large highly dimensional dataset as long as the computational cost remains acceptable. 
