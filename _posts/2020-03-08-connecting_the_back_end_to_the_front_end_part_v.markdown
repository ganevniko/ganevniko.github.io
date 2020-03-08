---
layout: post
title:      "Connecting the back end to the front end – PART V"
date:       2020-03-08 23:57:10 +0000
permalink:  connecting_the_back_end_to_the_front_end_part_v
---

This the fifth part of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user and return a model prediction or other output of your choice. In last week’s post I went over the steps needed to create the flask  web application which displays a form on a web page to collect input data from the user. Once the inputs are received, the web app sends a request to REST-Api in the back end to obtain a prediction and serve it back to the user. In today’s blog I will be using various techniques to run some tests on our API application to make sure it is running as expected. I will show how to test the API using Postman or the “requests’ library.

As a reminder, here is the code for our REST-Api running on port 3000:

![](img/124.png)

<b><u>Postman</u>

Postman is a platform for API development, it is widely used in the industry to test APIs before they go intro production. You can download postman form their official website at the following link: [https://www.postman.com/](https://www.postman.com/). Once downloaded and installed, it we are going to use it to make sure the flask RESTful API we created above works as expected. The home page should look as shown below:

![](img/125.png)

Click the plus icon on the top left as indicated on the screenshot to be ready to write a new request. Also not that inside our “sample_model” class in python we only have a get function so we will use the get method to test the API. The API takes two inputs in the following format, (input1,input2),  to return the result. After selecting the method you want to use, just type in the address of the server you are running the API on, in this case your AWS EC2 instance IP address and click send. Our class multiplies the two inputs so we are expecting to see the result of this multiplication returned at the bottom. Please note that I am using 127.0.0.1 in this example as the IP because I am running it on my localhost. 

![](img/126.png)

As you can see above, we received the expected response in postman and we are now confident that our API works as expected. Postman is a great tool for testing APIs and it is widely used but if you only going to run one or two tests and don’t want to go through the installation process, you can also test your API using a simpler tool as the “requests” library in python.

<b><u>Requests Library</u>

Start by using pip to install the library and importing it. I like to import it as “re”. You can then send your get request as below, I am here using 25 and 12 as the sample inputs. 

![](img/127.png)

This request will return the code of the response received from the flask server. The response should be 200, meaning that it was successfully processed. If we want to see what the content of the response is we can just add content at the end of our request as below:

![](img/128.png)

I added the string formatting just to clean the result a little which will come useful in the next steps when we are feeding this result to the web application for serving to the user.

<b><u>Conclusion</u>

In this blog we reviewed how to troubleshoot our REST- Api to make sure everything is working as expected. The tools used here will come in handy as you develop more complex APIs and add many features to them. Postman is the go to for many API developers but if you need to run a quick and simple test do not hesitate to just import the “requests library”.




