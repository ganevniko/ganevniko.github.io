---
layout: post
title:      "AWS - Using Athena to query data stored in S3"
date:       2019-11-04 15:19:59 +0000
permalink:  aws_-_using_athena_to_query_data_stored_in_s3
---


Amazon defines Athena as “an interactive query service that makes it easy to analyze data directly in Amazon Simple Storage Service (Amazon S3) using standard SQL”. Unlike other SQL query engines, Athena is limited to files stored in AWS S3 only and is capable of handling a variety of file formats such CSV, JSON, Parquet…

![](img/56.png)

The code above will create a CSV file with data on one hundred randomly generated users. And the next step would be to upload that to an S3 bucket. I have prepared a few lines of code to that straight from your Python IDE assuming you have your AWS credentials and you have created a bucket ready to host the data.

![](img/57.png)

Now that we have the file in S3, we are ready to open up AWS and create a table. We will achieve that thanks to AWS Glue crawlers. A crawler can crawl multiple data stores in a single run. Upon completion, the crawler creates or updates one or more tables in your Data Catalog. 

<b><u>Creating a database and an AWS Glue Crawler</u></b>

In your AWS console click on the Services tab and type AWS Glue. You should land on a page looking like this.

![](img/58.png)

Next select add tables using a crawler and pick a name for your crawler, I named mine test_crawler. After clicking next, the following screen will prompt you to select the data source, select Data Stores and click next. On the following, select S3 as the data source and pick the source bucket as shown below, then click next.

![](img/59.png)

Next you will be prompted to choose an IAM role, you can either create a new role or use an existing one based on your preferences. You will then be asked for the frequency at which you want the crawler to go through your S3 bucket to update the database. For the purposes of this exercise, let’s keep the default selection of ‘Run on demand’. At last you have to decide of the output of the database, all you have to do is select a name for your database and click next. Following a review of all your settings you can save your selections and the database and crawler will be created. In this example I called my database sample_userdb.

<b><u>Creating the table to query</u></b>

You can now go back to AWS console Services drop down and select AWS Athena. Unfortunately you are not ready to query the database yet, you first need to create a table to query from. Ones in Athena, select your database on the scroll down on the left. You are then prompted to create a table. Select the database we created and give a name to your table. In order for the console to accept your setting you will need to make sure to type in the bucket name respecting the format shown below. 

![](img/60.png)

On the next page select the format of your data for example CSV in our case. And you will then have to create the columns for your table. I chose to do it in bulk but you can create them one by one. 

![](img/61.png)

Your table is now created and you can run SQL queries on it using Athena as shown below. 

![](img/62.png)

<b><u>Conclusion</u></b>

In this blog we learned how to generate a database of random users in S3 and create an AWS Glue crawler to update this database as needed. We then used Athena to run queries on this database and save them back to S3. 
