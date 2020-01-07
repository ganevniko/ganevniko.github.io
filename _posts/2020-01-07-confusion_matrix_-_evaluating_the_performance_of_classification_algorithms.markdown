---
layout: post
title:      "Confusion Matrix - Evaluating the Performance of Classification Algorithms "
date:       2020-01-07 14:42:01 +0000
permalink:  confusion_matrix_-_evaluating_the_performance_of_classification_algorithms
---


After cleaning our data, engineering all the features and choosing the appropriate model and parameters to make predictions, we need to get an understanding of how well our model performed. If this model happens to be a classification model,  the Confusion Matrix will be our best asset. This tool intends to calculate statistics on how well our classification model performed in order for us to be able to determine which model of our models did the best and pick the one to use a production environment. In this blog we I will explain how the confusion matric works and how to calculate it for a 2-class classification problem.

<b><u>Understanding the confusion matrix</u></b>

The confusion matrix is basically a table with four different categories of predicted and actual values. These categories are the True Positive (TP), False Positive (FP), True Negative (TN) and False Negative (FN). Below is a illustration of a typical confusion matrix.

![](img/88.png)

Let’s try to understand what these four different categories mean with the example of cancer detection using imaging.

<b><u>True Positive (TP): </u></b>The model predicted positive and it is true. In other words, given the image, the model determined the person is ill and that was truly the case. 

<b><u>True Negative (TN):  </u></b>The model predicted negative and it is true. In other words, given the image, the model determined the person is not ill and that was truly the case.

<b><u>False Positive (FP) or Type I Error:  </u></b>The model predicted positive, but it is not true. In other words, given the image, the model determined the person is ill but that was actually not the case. 

<b><u>False Negative (FN) or Type II Error:  </u></b>The model predicted positive, but it is not true. In other words, given the image, the model determined the person is ill but that was actually not the case.

<b><u>Performance metrics for a 2-class classification problem</u></b>

The confusion matrix is most useful in calculating performance metrics and depending on the problem we are trying to solve the performance metric that will be the most important to us will vary. These performance metrics are recall, accuracy, precision and the F-Measure. 

<b><u>Recall</u></b>

![](img/89.png)

Recall is a measure of the proportion of positives we correctly identified to all the positives in our training set. In the cancer detection we used above recall would be the performance metric of choice because our focus is to not let any ill patients slip through the cracks. For example, if 1% of the population is ill and our model classifies all our images as healthy, it will be right 99% of the time but recall will be zero. 

<b><u>Precision</u></b>

![](img/90.png)

Precision is a measure of the proportion of positives we correctly identified to all the positives predictions made by our model. 

<b><u>Accuracy</u></b>

![](img/91.png)

Accuracy is a measure of the proportion of correct predictions (positive or negative).

<b><u>F-Measure</u></b>

![](img/92.png)

The F-Measure or F-Score uses Harmonic Mean in place of Arithmetic Mean by punishing the extreme values more. It is very useful in situations where we are comparing two models with low precision and high recall or vice versa. 
