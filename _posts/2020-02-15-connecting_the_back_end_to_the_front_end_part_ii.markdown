---
layout: post
title:      "Connecting the back end to the front end – PART II"
date:       2020-02-15 17:54:23 -0500
permalink:  connecting_the_back_end_to_the_front_end_part_ii
---



This the second part of my blog series on to how to deploy two simple flask application on an AWS server and make them communicate with each other to process inputs provided from an end user, and return a model prediction or other output of your choice. In last week’s post I went over the steps needed to start an AWS EC2 instance with Ubuntu 16.04, I hope your instance is now up and running and you are ready for the next steps. At the end of the previous part I provided a link to [https://www.putty.org/](https://www.putty.org/) for you to install the tool. This tool will be used to access the EC2 instance through SSH connection using port 22 (standard port for SSH). I want to specify that this is for Windows users only, MAC users will SSH into the instance using different software or simply the command line. In this part I am explaining how to access the instance and install everything we need on it to be ready to deploy our flask apps. 

Once the tool is installed and open, it should look like that:

![](img/112.png)

In the Host Name field, we need to enter the DNS of our EC2 instance which could be found on AWS. In order to find your host name, open the EC2 dashboard as we did previously and select the EC2 instance you created. The host name is located at the bottom under Public DNS (IPv4) as shown below:

![](img/113.png)

Copy the DNS to your clipboard and paste it in the Host name field of the Putty tool. The next step is to provide the path to the access key that was saved in a .pem file when we first launched our EC2 instance. I mentioned in the previous blog that you will need this file to access the instance. Click on the SSH tab in the menu of the Putty tool and then go to Auth and browse to the .pem file. You are now ready to SSH into you instance once you click on open. See below for an illustration of these instructions. 

![](img/114.png

There will be a warning message which is normal, select ‘Yes’.

![](img/115.png)

The last step is to enter the username once the SSH window opens. The standard username is Ubuntu, type it in and press enter. <strong>CONGRATULATIONS! You have just SSHed into your EC2 instance for the first time!</strong>You should see the following shell: 

![](img/116.png)

It is now time to use some basic linux instructions to set up the instance. I am far from being a Linux expert but I will go over some basics. The command ‘sudo’ is used at the beginning of each instruction to indicate that you are using your root user rights. The first thing we are going to do is update you instance with the following command:

<strong>sudo apt-get update</strong>

Now that our server is updated, we are ready to install python and everything else we will need to run our flask applications. Let’s start with python.

<strong>sudo apt install python3-pip python3-dev build-essential libssl-dev libffi-dev python3-setuptools</strong>

Finally before we install our python libraries like flask let’s first create a virtual environment. We first install virtual environment tool then create an environment named “virtenv” in our project folder that we will  call project.

<strong>sudo apt install python3-venv</strong><br>
<strong>mkdir project</strong><br>
<strong>cd project</strong><br>
<strong>python3 -m venv virtenv</strong><br>

Now activate the virtual environment:

<strong>source virtenv/bin/activate</strong><br>

And install flask and flask-restful into it:

<strong>pip3 install flask</strong><br>
<strong>pip3 install flask-restful</strong><br>

<b><u>Conclusion</u>

In this blog we learned how to access our EC2 instance from windows using the Putty tool and we installed all software need as python and all other packages. We created a virtual environment for our app in the project folder and are now ready to create flask applications and flask restful APIs which we will start doing in the next part.








