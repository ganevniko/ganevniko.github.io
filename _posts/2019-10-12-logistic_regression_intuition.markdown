---
layout: post
title:      "Logistic Regression Intuition"
date:       2019-10-12 18:45:26 +0000
permalink:  logistic_regression_intuition
---


*‘In statistics, the logistic model (or logit model) is used to model the probability of a certain class or event such as pass/fail, win/lose, alive/dead or healthy/sick. This can be extended to model several classes of events such as determining whether an image contains a cat, dog, lion, etc... Each object being detected in the image would be assigned a probability between 0 and 1 and the sum adding to one’ - Wikipedia*

In other words logistic regression determines the probability of a data point to be part of a certain class within a binary classification model or a multivariate classification problem.  This model will allow us to solve many problems: how does an additional pound of weight increase chances of a heart attack? How does age influence the probability of having cancer? How does salary influence the probability of repaying debt? And many others.  Let’s take the example of salaries and debt repayment with the following data frame and its visualization: 

![](img/46.png)

Or binary outcome target here is “Does the person repay their loan?”. We have only two possible outcomes: ‘Yes’ and ‘No’. While linear regression gives us results in terms of a real number, logistic regression works in terms of probability values which assigns the result to a discrete class. For example the plot above shows green able to pay back and red unable. In order to obtain the probability values needed to classify the data points, logistic regression uses the sigmoid function to transform the inputs. This function takes any real value and returns a value between 0 and 1 as shown below:

![](img/47.png)

Once the inputs are transformed into probabilities, we chose a threshold and say for example if the probability is more than 0.5 it’s labeled ‘Yes’ or one and if it is less than 0.5 it is labeled ‘No’ or zero. In the above formula of the sigmoid function, ‘t’ represents for example the equation from a multiple linear regression.

Multivariate linear regression equation:
ŷ i=Xi1∙w1+Xi2∙w2+Xi3∙w3+...+Xin∙wn

Multivariate logistic regression:
P(class=1) = 1/(1+e- ŷ i)  where  ŷ i=Xi1∙w1+Xi2∙w2+Xi3∙w3+...+Xin∙wn

**Cost Function**

For Logistic regression the loss is cross-entropy. It calculates the quantitative difference between the distributions: we use it to understand how close the predicted distribution is to the original one.  Without getting into too much detail of how this function works let’s just have a look at the formula: 

![](img/48.png)

When discussing logistic regression, please make sure to distinguish between multivariate logistic regression and multiclass logistic regression classification. In our previous example we have a multivariate binary classification logistic regression because we have multiple independent variables (loan amount and salary) but only two outcomes: repaid or not repaid. An example of a multivariate multiclass classification logistic regression would be for example a model using the color and shape of a fruit to determine if it is an orange, an apple or a tomato. 

Once the loss function is calculated it needs to be minimized to find the most correct weights and the best candidate for this task is as always gradient descent. 

**Advantages**

One of the advantages of linear regression is interpretability because we are getting optimal weights which demonstrates the importance of each features. Also this methods gives us probability scores which is useful because we can see how close the probability is to another class .<br>
A major strength is that it is very easy to implement and easy to explain to non-technical audience.

**Disadvantages**

Curse of dimensionality and categorical feature issues. The model tends to achieve poor results when given data with high dimensionality. And if you hot encode too many categorical variables you end up with many columns resulting in high dimensionality which is not greatly compatible with the model as stated previously.  




