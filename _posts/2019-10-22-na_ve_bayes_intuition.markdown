---
layout: post
title:      "Naïve Bayes Intuition"
date:       2019-10-22 11:54:57 -0400
permalink:  na_ve_bayes_intuition
---

The Naïve Bayes algorithm is a classification technique based on the Bayes’ Theorem which assumes there is independence between the features. We interfere with applications utilizing this algorithm on a daily basis, for example it powers recommendation systems for streaming applications or adds on social media as well as many online retail websites. <br> 
Naive Bayes model is easy to build and particularly useful for very large data sets. Along with simplicity, Naive Bayes is known to outperform even highly sophisticated classification methods. Let’s have a look under the hood of this major classifier.

<b><u>The Bayes Theorem:</u></b>

It is one of the basic theorems in the elementary probability theory: it explains the probability of an event based on a combination of prior information that might be related to that event, and new information. 


![](img/49.png)

Prior probability: the Bayes theorem starts with probabilities of specific events of interest based on historical records or data. Everybody will agree that our belief about uncertain events can change as new information becomes available. For example you might be 95% certain that your home soccer team will win there game today, but after they are losing two to nothing at the end of the first half you might drop that to a shy 93%.


<b><u>How does the Algorithm Work? </u></b>

The first step is to convert the data to a frequency table before creating a likelihood table. 

![](img/50.png)

In the example above, we are working with conditional probabilities to determine the likelihood of a random person owning a car based on the city that they live in. <br>
The data from the initial table allowed us to build a distribution table, and a likelihood table. The likelihood table gives us the conditional probabilities. For instance, the probability of a person owning a car given they are living in New York City is 2/7 while the same probability for someone who is living in Jersey City is ¾. <br>
We are now ready to use the Bayes theorem with the formula presented earlier to calculate the posterior probability for each class, and pick the one with the highest posteriori probability as the predicted outcome. 


<b><u>Advantages </u></b>

Some advantages of the Naïve Bayes classification algorithm are that it is fast, and easy to code. This algorithm also works on small datasets with not much information which can make it your go to choice in many situations where you are building new features and don’t have much data yet. The fact that it is also easy to understand will make this classifier your one of you best assets during business presentations in front of non-technical stakeholders.<br> 
Finally Naïve Bayes performs well when faced with high dimensions where many others tend to fail.


<b><u>Disadvantages </u></b>

On the disadvantages side, the Naïve Bayes classification algorithm is thrown off by the zero conditional probability problem, where if one of the terms in the numerator is zero, then the probability will be zero. Also, the algorithm can be tricky to use with continuous features, it only accepts discrete values forcing you to use binning for continuous values which could result in loss of data. And finally, one of the main disadvantages of the Naïve Bayes classification algorithm is Naivety. This mainly comes from the assumption that the features do not depend on each other which is rare when working with real world datasets.

<b><u>Source </u></b>

[https://medium.com/@Mandysidana/machine-learning-types-of-classification-9497bd4f2e14](https://medium.com/@Mandysidana/machine-learning-types-of-classification-9497bd4f2e14)

