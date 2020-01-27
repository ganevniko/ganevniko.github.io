---
layout: post
title:      "Serving a python/flask application using WSGI "
date:       2020-01-27 23:32:31 +0000
permalink:  serving_a_python_flask_application_using_wsgi
---

Deploying your flask application to a webserver as a web application or a REST-Api are the most common and recognized ways of serving your application and showing your work to the public. This task can also prove to be very challenging when you must do it for the first time. In this first blog about flask REST-Api deployment I will show some of the basics and keep you updated on my findings with a second part in the near future.

Before we dive into how it works, lets first look into some vocabulary because when working with WSGI the terminology can easily get confusing. WSGI with all cap letters would typically refer to the protocol which can be perceived as a language used for the web server to communicate with application for example. On the other hand, when you see uWSGI that would most of the time mean that the writer is referring to a web server that implements the WSGI standard (speaks that language).  

WSGI is pronounced wiz-gee and stands for Web Server Gateway Interface, basically it is an interface that can be used to establish communication between a web server and a python application because web servers usually can not read python applications. 

We can test WSGI by creating a WSGI compliant server as uWSGI because it is fairly simple to set up. We will begin by installing uWSGI with the following command:

![](img/96.png)

Next, we can create a basic python application to test if our uWSGI server is working properly. This basic application can be just a function, but it is important that you call it “application” in order for it work. Below is a simple application that can be used as an example:

![](img/97.png)

I have saved the above python function in app.py, that allows me to run the uWSGI server using the following piece of code:

![](img/98.png)

Congratulations! The “Hello World!” is now deployed on our server and running on port 5000, you should be able to access the IP address of your server on port 5000 and read “Hello World!” on the page accessed. Now let’s see if we can do the same with a Flask app with the code below.

![](img/99.png)

Flask exports its WSGI function that we previously called application as app, so we need to provide uWSGI with appropriate information to be able to use the correct function. The code below should make it work. There are a few more setting on this line of code but I won’t be going over them in this blog. I will be making a deeper dive on uWSGI in an upcoming blog.

![](img/100.png)

<b><u>Conclusion</u></b>

In this blog I have illustrated the basic settings and commands needed to deploy a simple python or flask app using WSGI. WSHI is extremely rich and powerful and we have barely scratched the surface here. Finally, once your app is properly running on this server what you can do is set up your server to run the command as soon as it starts, and it would most likely work good enough if you are just testing. I would not recommend deploying this way for production, instead nginx can be the solution in addition to uWSGI. 

<b><u>Sources:</u></b>

[https://www.ultravioletsoftware.com/single-post/2017/03/23/An-introduction-into-the-WSGI-ecosystem](https://www.ultravioletsoftware.com/single-post/2017/03/23/An-introduction-into-the-WSGI-ecosystem)

[https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html](https://uwsgi-docs.readthedocs.io/en/latest/WSGIquickstart.html)






