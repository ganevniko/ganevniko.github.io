---
layout: post
title:      "A/B Testing on Microsoft's Northwind Database "
date:       2019-02-06 21:11:28 +0000
permalink:  a_b_testing_on_microsofts_northwind_database
---

The Northwind database is a free, open-source dataset created by Microsoft containing data from a fictional company. In my analysis of this database the goal is to practice gathering information from a real-world database and use my knowledge of statistical analysis and hypothesis testing to generate analytical insights that can be of value to the company. The main tools that I will utilize are SQL queries to read the data base, formulating hypothesis and testing statistical significance of the results with various techniques like F-Test through Analysis of Variance (ANOVA) and T-statistics combined with P-Value at default level of significance of 5%. Below is the ERD for the database: 

![](img/43.png)

<u><b>Exploratory Data Analysis</b></u>

Before jumping into formulating questions and hypothesis to answer them an exploratory data analysis (EDA) of the database is necessary to  ease the navigation through the data when generating insight for the company. After connecting to the database, the first query I ran was:

*SELECT name FROM sqlitemaster WHERE type='table';*

Combining this query with the ‘.fetchall()’ function returns a list of the table names inside the SQL database. The tables are not necessarily named the same way as on the diagram and knowing the exact names is crucial to writing queries and being able to read the database. We notice for example that the orders table was labeled ‘Orders’ on the diagram but is actually called ‘Order’ without the ‘s’ at the end in the database. This rises two issues: we need to remove the last letter and also use brackets when we call this table because order is a command word in SQL and the brackets will let the program know we are using it as a name not as a command. 

The next step in the EDA stage is to check for normality. Since most of our questions will be centered around the quantity ordered we want to make sure that quantities are normally distributed or at least normally enough for our hypothesis testing to be reliable. The sample we are focusing on are orders from the order details table where the discount is not zero. Using seaborn to plot the sample we notice significant skewness and slight kurtosis.

![](img/44.png)

One way to determine if this deviation from normality is going to significantly affect our results when testing the hypothesis is to use a Kolmogorov-Smirnov test. This test is going to return a d-statistic which represents the distance or difference between the cumulative distribution function of the sample and a normal distribution with same mean and standard deviation as the sample. The two cumulative distribution functions being close and the d-statistic being low we reject the hypothesis that the two distributions are significantly different and conclude that the hypothesis testing will be reliable.

![](img/45.png)

<u><b>Is there a Statistically significant difference in quantity ordered when there is a discount compared to no discount?</b></u>

To answer this question, our null hypothesis states that discounts have no effect on the number of products customers order. We are going to use a t-test to decide if we can reject the null hypothesis. 

The first step is to determine the critical t-value. It could be done by looking at the table but the Scipy library offers an even easier way to obtain this critical t-value by using the ‘stats.t.ppf’ function. This function requires as first argument one minus the significance level and the degrees of freedom as second argument. In this example we are obtaining a critical t-value of 1.647 for a significance level of 5%. 

The second step is to calculate the t-value and p-value (level of significance) for our sample mean before comparing it to the critical values. Once again the Scipy library offers a great tool to obtain these statistics. The “stats.ttest_1samp” function requires the sample data as first argument and the population mean as second argument and returns a list with two elements: the first being the t-value and second the p-value. If the p-value is lower to our significance level we can reject the null hypothesis. Because the p-value for the first hypothesis comparing the mean quantity per order to the mean quantity of orders with discounts is very close to zero, we reject the null hypothesis and conclude that the mean number of articles sold on orders with discounts is statistically significantly higher than the mean number of articles sold on orders without discounts at a significance level of 1% or even less.

<u><b>Does the amount of the discount matter?</b></u>

Using the same method as for the previous question, we test each discount level quantity mean against the population mean. Since all the values are statistically significant at a significance level of 5% or less, we can say at that level of confidence that the actual amount of the discount does not really matter as long as there is a discount. Note that the values for 1%, 2% and 3% discounts are not reliable because only a few orders with these levels of discounts are available. More data would be needed.


<u><b>Is there a statistically significant difference in discount between categories?</b></u>

To answer this question the null hypothesis will be that there is no difference in discount level between categories and we will use analysis of variance (ANOVA) to test the hypothesis. The “anova_lm” function of the Scipy library allows to build an ANOVA table and determine if we can reject the null hypothesis. ANOVA uses an F statistic similar to the t-statistic we used before and also has a level of significance similar to a p-value. In our example this level fo significance is over 14% which means a 14% chance of type I error or in other word incorrectly rejecting the null hypothesis. Since the risk of Type I error is much higher thant what we are willing to accept we fail to reject the null hypothesis and conclude there is no statistically significant difference in discount level between the eight categories at the 5% significance level, no post hoc test required.


<u><b>Do discounts increase quantity of product purchased in an order?</b></u>

In this question we will group the data per product id from the Products table and compare the mean of each product ordered when it was discounted to the mean of this product when ordered without discount and look at p-values as previously. We already determined that giving discount significantly increased the quantity ordered, this time the goal is to determine if discounting a product increase the quantity people will buy of that same product. The null hypothesis is that there is no difference in quantity of a single product purchased in an order due to discount on that same product. After calculating the p-values we fail to reject the null hypothesis for all 77 products. There is no statistical difference at the 5% level of significance in the number of single product customers will order on the same order whether there is a discount on them or not. In other words, statistically speaking, people won't buy more of the same because it's discounted, they will use the money to buy other products.


<u><b>Are there regions where discounts have a significantly higher effect on quantity purchased compared to the other regions?</b></u>

We are going to compare the mean quantity on discounted orders in each region to the mean quantity on discounted orders in all regions combined. A t-test rejects the null hypothesis at the 5% level of confidence for the region of North America only, where quantity purchased when there is a discount is statistically significantly higher compared to quantity purchased in other regions when there is a discount.

<u><b>Can we find geographical areas as small as zip codes that order significantly higher total quantity of products</b></u>

Using a t-test again we compare the average total quantity of products ordered per order and per zip code to average quantity per order. Since all the values are statistically significant at a significance level of 5% or less, we can say with that same level of confidence that there is no zip code that stands out when it comes to quantity ordered. The zip code level might be too restrictive, too detailed for the analysis, we can try analyzing per city or country.




