---
layout: post
title:      "Connecting the back end to the front end – PART III"
date:       2020-02-26 04:02:18 +0000
permalink:  connecting_the_back_end_to_the_front_end_part_iii
---

This the third part of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user, and return a model prediction or other output of your choice. In last week’s post I went over the steps needed to connect to our EC2 instance through SSH connection on port 22 and install all the needed packages as well as setting up a virtual environment we called virtenv. In this week’s blog we will be writing a simple flask api. 

If you are moving to this third part right after you have completed the second one you should already be in the virtual environment. If you have closed the SSH connection and reopened a new shell, please make sure to activate the virtual environment first using :

<b><u>source virtenv/bin/activate</u>

We are now ready to start writing the application. I use the command “sudo pico filename.extention” to write a file in the ubuntu server.

<b><u>The Rest-Api</u>

I will be showing the steps on a Jupyter notebook but they should be typed on the Ubuntu server using the “sudo pico” command. The first step is to import flask and flask-restful and the method we will be using:

![](img/117.png)

The next step is to create an app instance and an api for it as below:

![](img/118.png)

We then create a basic class that returns the square of a number, this function will be served by our sample api:

![](img/119.png)

We now need to add the endpoint associated with this class:

![](img/120.png)

And the last step for this api is to run on one of the ports we previously opened, for example port 3000:

![](img/121.png)

<b><u>Conclusion</u>

This week’s blog is a short tutorial on how to write a simple flask api. This api will be put to use along with the flask web application we will be deploying next week to make the two application interact with each other based on user input.

