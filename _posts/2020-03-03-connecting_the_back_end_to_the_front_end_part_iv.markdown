---
layout: post
title:      "Connecting the back end to the front end – PART IV"
date:       2020-03-03 15:35:34 -0500
permalink:  connecting_the_back_end_to_the_front_end_part_iv
---




This the fourth part of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user and return a model prediction or other output of your choice. In last week’s post I went over the steps needed to create simple flask API which just returns the square of a number, but this square function could be replaced by any AI model to serve projections. In today’s blog we are going to be writing some python and HTML code to build the front-end API that will be accessed by the user’s browser and return the results to that browser.  We will start by writing a simple HTML page that offers a form to the user where they can provide their input and then this same page will show the predicted result.

<b><u>The HTML page</u>

I am going to keep very simple here not only because it is not the purpose of the exercise but also because HTML is not my forte. The goal is to create the most basic HTML page offering a form that allows our user to enter some inputs. I will just start with a heading “This is our basic front-end user interface.” and then get started with the form. Note that for the form we need to specify the “POST” method and give a name to the data we are looking to collect to we can refer to it by this name later to integrate it in python. In the example below, I called my input “indata”.  

![](img/122.png)

You can type this html file using the “sudo pico index.html” command as we did in the previous blog. I called it index.html but you can call it anything you want as longs as you keep the name consistent across the different parts of our app. Also, make sure that you create a subfolder called templates inside your app folder where you place this index.html file, otherwise flask won’t work the way we want.

<b><u>The flask web application</u>

This time we won’t be creating an API as before but just a plain flask web application than will call the API we previously created. The endpoint I am using here is (‘/’) on port 3001 which we opened in the first part of the blog. Note that you have to replace localhost in the URL calling the API by the IP of your AWS Ubuntu server. Below is the code for the web app:

![](img/123.png)

Once you have both apps running you should be able to access the URL on port 3001 using your browser to make predictions.


<b><u>Conclusion</u>

In this blog we wrote the front-end HTML code as well as the flask web app that operates this front end and we connected that to our backend API. The cycle is now completed, and we are ready to run some test and try our application. Please note that for now you need to rush two SSH shells to run both apps, we will see how to change that in the next parts of this blog. 

