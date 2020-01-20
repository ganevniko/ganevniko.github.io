---
layout: post
title:      "Ensemble algorith with decision trees - Bagging"
date:       2020-01-20 19:38:43 +0000
permalink:  ensemble_algorith_with_decision_trees_-_bagging
---


In a previous blog I discussed how decision trees work and how they are used. Unfortunately, even if decision trees can find complex dependencies in a data set, they tend to be highly unstable and sensitive to minor changes in the dataset. In other words, they are easily overfitted. A common way to get around is issue is to use bagging, and in this blog I will discuss how bagging algorithms works.  

Bagging is basically following the idea of the wisdom of the crowd: it improves the performance by combining many estimates. How do you obtain a crowd of data sets out of a single one? Bootstrapping! Decision trees change dramatically if the sample is changed and bootstrapping is a method to generate subsamples with replacing, we basically multiply the quantity of data we have on hands with bootstrapping by generating new sets with replacing. The diagram below attempts to illustrate that process.

[](ing/94.png)

In bagging, for each bootstrap subsample we are going to build a new tree. For example, if we have one original dataset with n number of elements, we will create a certain number of subsets of n elements each and then build a unique decision tree specifically for each subset. We train all those trees independently and lastly, we find the average for each classifier. The only parameter used in the process is how many trees we want to include, and it is seeming to be best to increase the number of trees slowly until we get the best performance, measured by cross validation for example. One of the strengths of bagging algorithms is that they handle categorical data very well and require little to no data preparation. On the other hand, once you have a multitude of trees resulting from bootstrapping subsets of data, it becomes slower to train the model and also harder to visually interpret it. Depending on the size of your dataset bagging can also turn out to be computationally expensive. 

The code below shows how we can use Scikit-Learn to create a bagged tree classifier by using the BaggingClassifier algoritm from sklear.ensemble. In this case data_train and target_train are our datasets in an example of loan repayment based on salary. The bagging algorithm returned an accuracy of 82% while the regular decision tree classifier had achieved only 70% with a number of estimators of only twenty which means that only twenty bootstrapped data subsets were built. With higher computational power it would be interesting to go from one to a thousand or more bagged trees to see how accuracy would evolve. The expectation is that it will increase rapidly to a certain level after which adding additional bootstrapped data subset won’t increase accuracy anymore. 

[](ing/95.png)

<b><u>Conclusion</u></b>

In conclusion, bagging allowed us to avoid the major downfalls of decision trees while still enjoying all of their advantages. This significantly improved performance comes at a computational cost. The next step is to build a random forest by choosing a random subset of feature to make it potentially relatively computationally lighter.

