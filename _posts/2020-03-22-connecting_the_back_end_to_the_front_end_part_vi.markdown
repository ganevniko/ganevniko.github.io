---
layout: post
title:      "Connecting the back end to the front end – PART VI "
date:       2020-03-22 23:30:22 +0000
permalink:  connecting_the_back_end_to_the_front_end_part_vi
---

This part six of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user and return a model prediction or other output of your choice.  In last week’s post I wrote an update to part four in order to split the web application into two pages. The first page will receive the inputs and the second one would deliver the predictions. The reason to make that split was to offer more flexibility as of the number of inputs in order for any reader to be able to use this template and framework in order to deploy any model into a web application with an API making the calculations on the backend. In a future blog I will show how to utilize what has built here to adapt it to any model of your choice by saving the model into an H5 file and making minor changes to the code we have built over the weeks in this blog series. This week we are going to make sure that everything works as we expect it to.

I will be share here screenshots of a Jupyter notebook because it is easier to read but all this files need to be written inside of our EC2 instance using for example the “sudo pico” command. The only difference between what I am showing what needs to be entered onto the EC2 instance is that you need to replace the local host IP address I am using here which is 127.0.0.1 by the IP address of your instance as shown in the first part of this blog series.

As a reminder here is our code for the API on the back end: 

![](img/132.png)

And here is a our code for the web application in the front end:

![](img/133.png)

Also the HTML page for the input referenced here as ‘index.html’ can be seen at this [following link](https://github.com/ganevniko/ganevniko.github.io/blob/master/img/129.png), when the HTML page delivering the prediction can be seen at by clicking [here](https://github.com/ganevniko/ganevniko.github.io/blob/master/img/130.png). 

What you need to do next is lunch both applications and make sure they are running on the appropriate ports. In this example I have used ports 5005 for the web application and port 5000 for the API. I f you have chosen to use different ports, please refer to the first part to see how to make sure the ports are open and accessible on your EC2 instance. For example the once starting the web application, this is what you should see on the screen:

![](img/134.png)

Please note that I am purposely keeping the debug mode off for the moment. Also this is not a production environment so the message you are getting is normal. You can read about how to set up a production environment in my blog about NGINX and WSGI. Once both applications are running you can open the IP address on the appropriate port this is what we should see:

![](img/135.png)

Remember our API here simple multiplies the two inputs, I am using 34 and 45 as my inputs here. After pressing predict, our application should return the following prediction: 34x45 = 1530.

![](img/136.png)

<b><u>Conclusion</u>

Our web application and API interact as we expected and deliver the result we wanted to see. Congratulation, you have a fully operating application and it can be used to deploy any model. In my next blog I will show how to utilize this framework to deploy a machine learning model saved on a H5 file.









