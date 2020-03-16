---
layout: post
title:      "Test post for today"
date:       2020-03-16 23:30:59 +0000
permalink:  test_post_for_today
---

This the fourth part of my blog series on how to deploy two simple flask applications on an AWS server and make them communicate with each other to process inputs provided from an end user and return a model prediction or other output of your choice. In last week’s post I went over the steps needed to create a simple flask API which just returns the square of a number, but this square function could be replaced by any AI model to serve projections. In today’s blog we are going to be writing some python and HTML code to build the front-end API that will be accessed by the user’s browser and return the results to that browser. We will start by writing a simple HTML page that offers a form to the user where they can provide their input and then this same page will show the predicted result.
