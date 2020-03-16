---
layout: post
title:      "Connecting the back end to the front end – PART IV Update"
date:       2020-03-16 00:22:59 +0000
permalink:  connecting_the_back_end_to_the_front_end_part_iv_update
---


This an update on the fourth part of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user and return a model prediction or other output of your choice. In part four of this blog series we wrote the code for our web application as well a our API. Last week we tested the API and everything was working as expected but before we test the web application I would like to make some changes to it. In this blog we will be updating the approach to our web page and split in two pages, one  receiving the inputs and one delivering the output. 

<b><u>Inputs page</u>

We will keep the code on this page very simple. All we are going to do is create a form taking two inputs named input1 and input2 as in part five of the blog. We have to make sure that the name of the variables is saved under input1 and input2 in order to for the API app to be able to process them correctly according to the code we wrote in part five. 

![](img/129.png)

The code above shows how our inputs HTML page is built. This HTML file needs to be saved inside a folder called “templates” inside the folder where the web application is running. We will be using the render_template method of the Flask framework to render the page. I saved this page as index.html. 

<b><u>Outputs page</u>

This HTML file also needs to be saved in the templates folder in order to be properly recognized and rendered by the Flask application. I have called it result.html, feel free to change the file’s name but make sure to reflect the appropriate name in the “/result” endpoint we are going to create next. Below is what my code looks like: 

![](img/130.png)

If you are an HTML expert, I apologize for my beginner skills and I am sure you would be able to do much better here but for the others that would do. The variable “value” is what we will be using to inject the prediction returned by the API.

<b><u>The Flask Framework</u>

Here are the changes I made to the web app in order to have two pages rather than one. The main motivation was to allow for as many inputs as needed to run your model. This new version of the app provides you with an example that would be reusable for a model utilizing as many inputs as needed. All you would need to do is add lines on the HTML inputs page. 

![](img/131.png)

Please note that I am using the local host’s URL because I was testing in this case on my local machine. You will need to replace it with your EC2 instance URL and the appropriate port. We were previously using port 3000. 
My preferred way is to write the code in Jupyter notebook and make sure it runs correctly then SSH into my EC2 instance and navigate to the appropriate folder where I use the “sudo pico” command to write a file and paste the code I copied from Jupyter. 

<b><u>Conclusion</u>

We now have all the pieces and we are ready to run our application. I will still run a test on the web application on the EC2 instance to make sure it is functioning properly in the virtual environment created there. 

