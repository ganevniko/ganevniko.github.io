---
layout: post
title:      "An Introduction to Cross Validation"
date:       2019-12-03 16:24:05 -0500
permalink:  an_introduction_to_cross_validation
---


Train/test splitting and cross validation are two very important concepts in data science that allow you to make sure that the model you trained is performing well on data it has never seen before and make sure you are avoiding or at least minimizing overfitting.

<b><u>What is overfitting?</u></b>

Overfitting occurs when the statistical model (linear regression, decision tree…) is performing very well on the training data but as soon as it is presented with new data the performance drops significantly. This usually happens when the model is too complex that is too say has too many features for example. The reason the model is performing poorly on the new data is because it can not generalize, it only works on the specific training dataset it was fitted on. Overfitting is a very common issue for data scientist. 

<b><u>What is underfitting?</u></b>

When a model in underfitted it means the model misses the training data. Once again, the model cannot be generalized to new data but this time it is because the model is too simple rather than too complex or simply inappropriate foe the task, for example imagine trying to fit an linear regression model to non linear data. Underfitting tends to be less of an issue than overfitting but both need to be avoided. 

![](img/69.png)

<b><u>The Train/Test Split</u></b>

When building a machine learning model, we split the data into a training dataset and a testing dataset. The training set contains a known output and the model learns on this data in order to be generalized to other data later on. Meanwhile the test set is kept on the side for the performance of the model to be evaluated on data it has never seen before. Below is an example of the most common way to split your data in train and test sets using Scikit-Learn library.

![](img/70.png)

<b><u>Cross-Validation or how to avoid both overfitting and underfitting</u></b>

Cross validation helps us estimate parameters and model’s quality in general. It allows us to check over-fitting and underfitting. Basically, it helps us determine the right test/train split to use. The concept is fairly simple: we take the data and make experiments where we select some of the data for testing and some for validation and compare the performance before deciding how to split our train and test data. The way we do It is the following:  we split our data into k subsets, and train on k-1 one of those subsets, then we use the testing subset to calculate the performance metrics we have selected like accuracy or recall. There are many different cross validation methods you can use and they are all described on the Scikit-Learn website here: [ https://scikit-learn.org/stable/modules/cross_validation.html](https://scikit-learn.org/stable/modules/cross_validation.html). Let’s describe the most commonly used method: the k-fold cross validation method. 

<b><u>K-Fold Cross Validation</u></b>

In K-Folds Cross Validation we split our data into k different subsets (or folds). We use k-1 subsets to train our data and leave the last subset (or the last fold) as test data. We then average the model against each of the folds and then finalize our model. After that we test it against the test set. 

![](img/71.png)

<b><u>Conclusion</u></b>

That was a short introduction to a very powerful tool which will help you in many situations. It allows you to optimize you model performance by selecting different combinations of train/test splits from your original data. Also keep in mind that the K-Fold cross validation method we referred to in this blog, as most cross validation methods, shuffles the data which is good for most datasets but not all. For example, if you are performing cross validation on time series you cannot shuffle the data and there are specific ways to performance the cross validation that I am planning to discuss in a future blog.  









