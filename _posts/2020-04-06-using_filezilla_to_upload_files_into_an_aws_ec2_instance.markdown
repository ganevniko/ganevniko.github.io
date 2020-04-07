---
layout: post
title:      "Using FileZilla to upload files into an AWS EC2 instance"
date:       2020-04-07 03:09:11 +0000
permalink:  using_filezilla_to_upload_files_into_an_aws_ec2_instance
---


I recently finished my blog series on how to deploy flaks applications on a Amazon Web Services (AWS) EC2 instance. In the process I showed how to write a flask API as well as a Flask web application and make them communicate through a webpage receiving user inputs and making requests to the API on the back end. In that process I mostly used the Linux command line and the “pico” command to type all kinds of files such as html or python files. Pico is very convenient for typing small simple files directly on your EC2 instance or other Linux operated system but once you want to start writing longer more complicating files it could turn out to be fairly challenging. In this blog I will discuss a software allowing you to write your files on your windows machine using a text or other file and upload them to your EC2 instance in an easy and efficient way. 

<b><u>Downloading FileZilla</u>

FileZilla is a free software and I would recommend downloading it from the official website here: [https://filezilla-project.org/](https://filezilla-project.org/). After opening this link you should get to this page: 

![img/142.png]

You need to download and install FileZilla client for the operating system you are using. For example I use Windows. The website should recognize you operating system and direct you straight to the appropriate version once you click on FileZila client. Once installed, click the FileZilla icon and you should get to the following interface:

![img/143.png]

<b><u>Uploading Files</u>

In the FileZila interface, select the “file” tab on top and then enter the “Site Manager”. Once open the Site Manager tab should look as below.

![img/144.png]

In red on this screenshot I have highlighted the fields we will need to fill in order to gain access to our EC2 instance. Note that I have already entered the User which is Ubuntu. This user is set up by default by AWS on EC2 instances allowing you to use that username as is. If you have created a different user or if you are using a different type of instance you will need to modify the username accordingly. We will need the hostname, key file and port to gain access. Next login to your AWS console here [https://aws.amazon.com/console/](https://aws.amazon.com/console/). Once in your console, navigate to your EC2 instance and copy the IP of the instance which corresponds to the hostname FileZilla is asking us for. If you are not sure how to find the IP of your EC2 instance on the console, or how to start an EC2 instance all together,  you can refer to Part I of my blog on Connecting the backend to the front end [here](https://ganevniko.github.io/connecting_the_back_end_to_the_front_end_part_i). As a reminder here is a screenshot to help find the IP address.

![img/145.png]

Next you have to make sure you are using an open port. For more info refer to Part I of my blog as indicated earlier. Finally you need to indicate the path to the key file to your EC2 instance that was provided by AWS when you first created the server. Explanation about this file are also available in Part I of my blog series on connecting the back end to the front end. You are now ready to access your instance in a Windows type interface. Click connect and you will have access! Congratulations! All you need to do is to navigate to the folder where you want to place a file on your instance and drag the file in it using your mouse as you would to on Windows or Mac. 

<b><u>Conclusion</u>

In this blog we learned how to use FileZilla, a very powerful free software allowing to navigate your AWS (or other) servers and instances. This software will come very handy when deploying more complex applications!


