---
layout: post
title:      "K-means Clustering Intuition"
date:       2019-11-19 14:18:08 -0500
permalink:  k-means_clustering_intuition
---


K-means is an unsupervised clustering algorithm designed to partition unlabeled data into a certain number (usually called “K”) of distinct groupings. In other words, k-means finds observations that share important characteristics and classifies them together into clusters. Clustering is used in market segmentation; where we try to find customers that are similar to each other in one way or another; for example, similar behaviors or geographic locations.

The most difficult part is to determine how many clusters or classes we are going to identify. Once we give the algorithm the number K, it is going to initialize the centroids, or centers of our clusters randomly. Ideally, they shouldn’t be absolutely random, we can make some general analysis and use intuition as well. 

![](img/64.png)

The next step is clustering or classification, we classify the dots by measuring the distance between the dots and the centroid. Distance here can stand of any similarity. Once we have these values we can proceed to centroids re-computation, that is to say we find a new position for the centroids by taking all the dots in the created cluster, find their mean and make that the new centroid.  We repeat the procedure until the difference of our centroids movements becomes minimal. Once the centroids become stable, it means we have found the right ones and there is no need to keep moving them. 

K-means Clustering is easy to code and understand, it is a great starting point for unsupervised tasks. Unfortunately, it is difficult to determine K and the experience is usually also not repeatable because we chose the initial centroids randomly. Finally rememebr that K-means clustering is mostly for numerical data and its usage for categorical data is very limited. 

<b><u>Sources:</u></b>

[https://towardsdatascience.com/k-means-a-complete-introduction-1702af9cd8c](https://towardsdatascience.com/k-means-a-complete-introduction-1702af9cd8c)


