---
layout: post
title:      "An introduction to SQL in Python"
date:       2019-12-23 03:41:24 -0500
permalink:  an_introduction_to_sql_in_python
---

In this blog we will be looking at SQL, a language that’s very important to learn when you’re working with databases. As usual, I want to give you aa 101 of both SQL and databases. You can achieve working knowledge of SQL with a fairly reasonable time investment if you do it right. Let’s have a look at it. 

<b><u>Databases : the basics</u></b>

Before we start pulling all the fancy data with a new toy, let’s understand what a database is. A database is an organized collection of data. This can be anything from financial data, students in a university etc. Databases are useful for pretty much every kind of company and institution and come in many varieties.

You may have seen things like Oracle, MySQL, PostgreSQL, etc when looking up databases or a tech blog. These are called relational database management systems. In short, software that allows us to create and manage databases. In this article I’ll be using  SQLite in Python. It is pretty easy to set up.

SQL is the language that talks to relational databases in order to store, update, change, and delete data. As to show you how it works, I’ll be creating a database in SQLite using the Microsoft Northwind Database. The diagram below is a representation of the database. 

![](img/80.png)

<b><u>Connecting to the database and creating the cursor</u></b>

The first thing we’ll do is create a database. We’ll just call it testDB.

![](img/81.png)

And done. The first line tells SQLite I want to connect to my database file ‘Northwind_small.sqlite” and then create a cursor that we will use to read data. Then I will recommend to list all the tables in the database to make sure the names and capitalizations on the database diagram are correct or you won’t be able to write appropriate queries.  

![](img/82.png)

<b><u>Structure of Queries</u></b>

As you may notice above, all queries end in semicolons. Queries are made up of statements, conventionally in upper case, that structure how you want the data returned. The four most common statements are:

1. SELECT: Choose this data
2. UPDATE: Change this data
3. INSERT: Add new data
4. DELETE: Remove this data

<b><u>Sample Queries</u></b>

We are now ready to start writing queries to return the data we are looking for. The most basic one would be a ‘SELECT’ to return an entire table, for example:

![](img/83.png)

Also, please note that I am only giving you the SQL query part but when using sqlite3 in python you always need to use the cursor and the .fetchall() method as shown previously.  I would recommend to tun a few basic queries as this one to start getting used to navigate the database. And now that you are more comfortable, let’s have a look at some queries that you are more likely to use in real life scenarios, such as:

![](img/84.png)

This query will return the listed columns from the respective tables. Note that the JOIN function is very useful to combine data from different tables and return in a new table based on a common column or so called key. For example, a company as Uber most likely has a database with all their trips and one of the columns of this database is the drivers id. On another table Uber is probably storing all their drivers. The common key in this scenario would most likely be the driver id and if you wanted to see for each trip where the driver lives for example, you would need to use a JOIN to combine information from both tables. 

<b><u>Conclusion</u></b>

I hope this blog was useful in getting started with SQL in Python using sqlite3. SQL is a must know for every data scientist even if you work for a larger company where there is a full time database manager. Also, the queries can get very complicated as you might find out during coding challenges as part of the interviewing process with some companies.

<b><u>Sources</u></b>
https://medium.com/the-data-logs/basic-sql-for-data-analysis-3c5624d06d3d<br>
https://en.wikipedia.org/wiki/Database<br>
https://stackoverflow.com/questions/12770521/reading-from-file-and-passing-value-as-parameter-in-sql/12771135<br>

