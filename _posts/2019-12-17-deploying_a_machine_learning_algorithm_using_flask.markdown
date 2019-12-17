---
layout: post
title:      "Deploying a Machine learning algorithm using Flask"
date:       2019-12-17 11:57:28 -0500
permalink:  deploying_a_machine_learning_algorithm_using_flask
---


There are a lot of resources online to learn how to train and develop machine learning algorithms but when it comes to deploying them the available information seems to be a lot sparser. For somebody as myself who does not have a software development background this crucial step of the process can prove to be as challenging as it is important to employers. In this blog I am going to assume that you already have a trained model and it is saved as pickle file named ‘model.pkl’.

<b><u>Creating the API</u></b>

The first step is to import the necessary libraries:

![](img/77.png)

Numpy will be used to turn the data provided by the requester into an array that the model can consume while Pickle is used to load our model. Flask is used to create the app and tun it on our server. And this what we will be doing with the following piece of code that creates a Flask() instance and loads the model.

![](img/78.png)

In the next step, we have bounded the API end point with the method predict(). In which the predict method gets the data from the json passed by the user. The model.predict() method takes the input from the json and converts it into a numpy array and the results are stored into the variable named output which is returned after converting to a json object using flasks jsonify() method.

![](img/79.png)

We are now ready to run our application with the .run() function, not that I will pass debug = True to be able to correct any errors as needed without restarting the server every time.  Also note that we use the default port 5000 and if __ name __ ==’__main__’ statement only indicates that we are running the module directly rather than importing it.

![](img/80.png)

Our server is now ready to accept requests to process data using our model from the model.pkl file. Let’s look at some code that would send a request to the server to get a prediction from our model.

<b><u>Making Predictions</u></b>

First we import the requests library that we will use for our POST requests, the requests.post() takes the URL and the data to be passed in the POST request and the returns the answer from the server which in our case is a prediction from the model.

![](img/81.png)

Please note that in this case the Url used will be localhost:5000 because we are running the application on our own computer on port 5000 which is the default port used by Flask, but we could have picked a different port if we wanted to. And finally, the code below actually sends the request for a prediction on a data point of ‘1000’, this is an arbitrary value I picked, depending on what your model is this data point can be virtually anything.

![](img/82.png)

<b><u>Conclusion:</u></b>

We have built in this blog a Flask Api to deploy our machine learning model build in Jupyter notebook using Scikit-Learn and saved as a pickle file. The next steps would be to turn it into a REST Api and run in on a server in the cloud, for example an AWS server. 



