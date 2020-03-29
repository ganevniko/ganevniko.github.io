---
layout: post
title:      "Connecting the back end to the front end – PART VII"
date:       2020-03-29 17:17:10 -0400
permalink:  connecting_the_back_end_to_the_front_end_part_vii
---

This part seven of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user and return a model prediction or other output of your choice. In last week’s post we finalized the model in the case of a generic model. The goal today is to build a model using scikit-learn and to deploy it simply using the frame we built in the previous series of the blog. I am going to start by building a simple multi-variate regression model using sickit learn and save it to a pickled file. Then  we will code the back end and frond end as previously to make available to the public.

<b><u>Building a simple multiple regression model</u>

Lets start by importing the necessary libraries. We will need a few to generate a set of random data that we will use for the regression. An alternative would have been to use a prebuilt data set from the scikit-learn library.

![](img/137.png)

Once all the libraries are imported we are ready to build ou model and save it to a pickle file. I won’t explain the process in details here because this is not the purpose of todays blogs.  Below is the code to generate the data, build the model and save it to a pickle file. 

![](img/138.png)

Note that this model uses two inputs, lets call these inputs “price”, “volume” to make the front end webpage look more realistic. 

<b><u>Building the back end API</u>

Here we will use the model we built previously but we need to add a few lines of code in it in order to load the pickled model and use it to process the inputs received from out front end web application. First, make sure to import the additional libraries the API will need to utilize. After importing Pickle and Pandas, instead of a simple multiplication we will load the model with pickle and use  it to predict the inputs form the user data.

![](img/139.png)

Please note that pandas is here used to transform the inputs into a format that will be acceptable for the scikit learn model to consume. 

<b><u>Building the front end API</u>

A few small changes will be needed on the front end. First always make sure that your URLs and ports match the IP address of your servers and that the ports are open. The second change involves naming and making sure all the variables naming correspond. For example we decided to call our inputs “price” and “volume”.

![](img/140.png)

Since we changed the variables names in the flask web application framework, some changes will be needed in the “infex.html” page for the application to function. As shown below, only fields names have changed.

![](img/141.png)

<b><u>Conclusion</u>

You are ready to run your app and allow anyone to use your regression model. This framework can be used for pretty much any model, you only need to save the model in a pickle file and adjust the number of inputs accordingly to the model you are deploying. Note that if your inputs require some processing before being fed to the model like scaling, normalization or PCA there will be a few additional steps to achieve that. 

