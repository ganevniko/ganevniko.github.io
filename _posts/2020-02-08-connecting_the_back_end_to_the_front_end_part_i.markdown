---
layout: post
title:      "Connecting the back end to the front end – PART I"
date:       2020-02-08 17:59:59 -0500
permalink:  connecting_the_back_end_to_the_front_end_part_i
---


In this blog series I will be using a few of the resources discussed in previous blogs and put them all together to show how to deploy two simple flask application on an AWS server and make them communicate with each other to process inputs provided from an end user. The first app will be a flask REST-Api making our processing and calculations on the back end. The second one will be a flask web application serving it to the public as an HTML page. By the end of the blog series you will have a fully deployed web app using an API on the back end to deliver results. The blogs will be broken down as follows:

<b><u>PART I ( this Part) </u>

* STEP 1 – Start an AWS EC2 instance and configure ports

<b><u>PART II</u>

* STEP 2 – SSH into the EC2 
* STEP 3– Install all resources needed on the EC2 instances

<b><u>PART III</u>

* STEP 4- Write our REST-Api 
* STEP 5 – Write the flask web application and HTML pages

<b><u>PART IV</u>

* STEP 6 – Test our application and conclusion

<b><u>STEP 1 – Starting an AWS EC2 Instance: </u>

In this step we will start an Ubuntu server on AWS. In order to do that you will first need to create an AWS account if you don’t already have one. You can do that with the following link [https://aws.amazon.com/console/](https://aws.amazon.com/console/). The signup process will ask for a credit card number but AWS won’t charge you anything for the resources we will be using in this blog as they are part of the free tier program offered to AWS users for the first three months. Please make sure to terminate the EC2 instances after you are done using them to avoid being charged in the future. If you are not sure how to terminate the instances you can reach out to me or just close your account all together.

Once you have created your account click on the services tab on the home page of the console and under the compute section select EC2 as shown below:

![](img/104.png)

You should now be on your EC2 dashboard showing no running instances. Click on the ‘Running Instances’ to get to the next page where you can select ‘Launch Instance’ to start a new server. The page should look as shown below:

![](img/105.png)

The instance type we will work with is an Ubuntu 16.04 server since it is free tier eligible. This server is a Linux server that we will set up in PART II by accessing it through SSH. I will go through each step of the process in details. Here are some screenshots on the next two screens in order to select the appropriate type of server . 

![](img/106.png)
![](img/107.png)

After you have selected your instance type, the following screen will ask you to create a key pair to be able to access it. I recommend to create a new key pair and save it on tour computer while making sure to remember where you saved it and the name of the file since we will need that file to SSH into the server.

![](img/108.png)

The last part of this step one will be to open one port for each of the two apps that we will be deploying on it. I chose ports 3000 and 3001 but you can use different ones if you like. In order to open the ports go back to the EC2 Dashboard from AWS console and click on ‘Running instances’ to see the list of your active instances as we did before. This time the list should not be empty: you have a running ubuntu server instance.  Click on the security group of the instance you created for this demonstration as shown below:

![](img/109.png)

Select the security group related to your instance and select ‘ Edit inbound rules’.  On the next tab we will open ports 3000 and 3001 to requests coming from any IP address (0.0.0.0). Click on ‘Add Rule’ and enter the ports information as shown below. 

![](img/110.png)
![](img/111.png)

Great, our EC2 instance is now running and the ports we are going to be using are open. The next step is to SSH into the instance and install python as well as all the other packages we will need. In order to SSH into the EC2 instance I will be using PUTTY. If you have never used PUTTY, start by installing it from [https://www.putty.org/](https://www.putty.org/). 

<b><u>Conclusion: </u>

This concludes the first part of this blog series on how to connect the back end to the front end and fully deploy a data science model or any other app on AWS and make it accessible to anyone. Next week’s blog will be focused on using the PUTTY tool we installed to access our EC2 instance through SSH and install python as well the other packages needed for our apps to run.


