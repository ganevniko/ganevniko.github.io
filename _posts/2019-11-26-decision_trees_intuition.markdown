---
layout: post
title:      "Decision Trees Intuition"
date:       2019-11-26 21:53:57 +0000
permalink:  decision_trees_intuition
---


*“A decision tree is a decision support tool that uses a tree-like model of decisions and their possible consequences, including chance event outcomes, resource costs, and utility. It is one way to display an algorithm that only contains conditional control statements.” - Wikipedia*

![](img/65.png)

In other words, decision trees can find very complex dependencies in a data set in a very simple way, they can be used to visually and explicitly represent decisions and decision making. So how does a tree split take place?

As shown below, a decision tree has a root, branches, nodes and leaves. The root is situated at the top, this root is related to internal nodes where the decisions are made, and the leaves are the final result of our classification or regression. 

![](img/66.png)

At each node the tree branches until we reach the leaf for each branch. The general rule is that each node should split the data set into different classes as cleanly as possible. The ideal situation is where a subset has all the objects belonging to the same class. In real life datasets we can measure the variation of responses in each subset using various criteriums of informativeness. 

<b><u>Gini Criterion</u></b>

The Gini criterion (or Gini index) measures measure the chance a specific data point being wrongly classified when it is chosen randomly. The index varies between zero and one where zero designates a pure class, that is to say all the elements belong to one class, and one means the elements are randomly distributed among various classes.

<b><u>Entropy criterion</u></b>

Entropy is nothing but the measure of disorder and its mathematical formula is as follows: 

![](img/67.png)

Entropy is generally measured between 0 and 1

<b><u>Information Gain </u></b>

Information Gain is the change in entropy after the split.

![](img/68.png)

We simply subtract the entropy of Y given X from the entropy of just Y to calculate the reduction of uncertainty about Y given an additional piece of information X about Y. The greater the reduction in this uncertainty, the more information is gained about Y from X.


<b><u>Variance Criterion </u></b>

The variation criterion used for regression problems. It is the actual variance of datapoints in the sub-sample because these data points are real numbers instead of classes. The smaller the variance the better the split. 

<b><u>When to stop splitting?</u></b>

You are probably wondering when you should stop growing your decision tree. One way of setting a limit to the growth of your decision tree is to set a minimum number of data points needed in order for the algorithm to perform an additional split. For example, if the resulting subset contains ten data points or less we stop splitting. Another rule could be to set a maximum depth of the tree which refers to the longest possible number of nodes between the root and the leaves. 


<b><u>Advantages:</u></b>

* It is very easy to interpret because it is well visualized. 
* It works with both numerical and categorical data. 
* Doesn’t require intensive data preparation.

<b><u>Disadvantages:</u></b>

* Overfitting is very common. 
* Data fragmentation problem, after each split the set becomes smaller which could induce bias in the model. 

