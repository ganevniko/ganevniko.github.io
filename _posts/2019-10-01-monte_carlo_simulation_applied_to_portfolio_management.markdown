---
layout: post
title:      "Monte Carlo Simulation applied to Portfolio Management"
date:       2019-10-01 17:46:33 -0400
permalink:  monte_carlo_simulation_applied_to_portfolio_management
---




Monte Carlo simulations perform risk analysis by simulating models of possible outcomes according to a chosen probability distribution for a parameter that has an inherent uncertainty. To get a basic understating of how it works we can use a simple example and calculate the area of a circle inside a square with a binary outcome experiment. Let say that we don’t know the value of Pi and want to calculate the area of a circle of diameter of one. We can draw a square around that circle and start randomly plotting dots inside that square. In this case we would be following a uniform distribution for the coordinates of the dots we are plotting. If the dot falls inside the circle we will label it a success and at the end we will estimate the area of the circle by dividing the number of dots inside the square by the total number of dots plotted. 

As we will see in the illustration below, the number of dots plotted is crucial to obtaining an accurate result. If we don’t plot enough dots the value is likely to be far from the actual value but with a large number of random values it appears very likely that we will get a number very close to the right answer. Python allows us to generate more than one hundred thousand outcomes in a significantly short period of time which makes it a powerful tool to run Monte Carlo simulations. By using the formula A = πr^2 the area of a circle with a diameter of one is approximately 0.785. Let’s use Python to code the experiment and see how close to this value we get with different numbers of random dots or different number of paths to say it in Monte Carlo words. <br/>

All we are going to do is go through a loop of ‘n’ number of paths and for each iteration we will generate two random values between -0.5 and 0.5 because our circle is centered on the origin. The first of this values will be the x axis value for our dot and the second one will be the y axis value. Using this coordinates we calculate the Euclidian distance of the dot to the origin. If the distance is inferior or equal to 0.5, our dot is in the circle, otherwise it is outside. Finally we divide the number of dots inside the circle by ‘n’ to calculate the area. The following few lines of code are enough to run the entire experiment. <br/>

![](img/24.png)

As shown above, one million paths give us a very accurate estimate of the areas, but let’s use matplotlib to have a look at what it took to get there by plotting all the random dots for different values of “n”.

![](img/23.png)

Now that we have a good basic understanding of how it works, I am sure that calculating the area of a circle or even estimating the value of Pi is not what most people reading this blog are looking to achieve. How can we apply Monte Carlo simulation to Data Science problems? Because of my background I will chose the finance industry to provide an example.

 It is well known that the stock market exhibits very high dimensionality due to the almost unlimited number of factors that can affect it which makes it an almost random variable, very difficult to model and predict. One relatively straightforward application of Monte Carlo in finance is optimization of a portfolio of stocks. Portfolios are built based on the Modern Portfolio Theory (MPT) by Harry Markowitz’s groundbreaking, Nobel Prize winning paper “Portfolio Selection” in 1952. 

I recommend to anybody interested in finance and portfolio theory to read about Modern Portfolio Theory by Markowitz but for the purposes of this blog we will keep it very simplistic. When picking a portfolio of stocks, you may be willing to take on different levels of risk depending on your goals. And here risk simply means standard deviation of returns. But regardless of your willingness to accept risk, you can maximize your returns by picking the combination of stocks that has the highest returns for this given level of risk or volatility. From here Markowitz’s idea is very intuitive: it only makes sense to invest in the portfolios, combinations of stocks, that have the highest returns for each level of risk and we are going to use a Monte Carlo simulation to simulate and plot thousands of portfolios and pick the ones with the highest returns by plotting returns against standard deviation. These portfolios are called by the author “The Efficient Frontier”. 

To illustrate the efficient frontier concept we will use four of the most common tickers in the Communication Services and Information Technology sectors: Netflix, Apple, Facebook and Google.

The idea is to use pandas to get historical prices for each of the above tickers and calculate daily returns and standard deviation. Then we will use a Monte Carlo simulation to assign random weights to each of these tickers in our portfolio (the sum of which will add to one) and plot the returns of each the portfolio against standard deviation. Note that from a return perspective, each stock contributes to the portfolio its daily returns times its weight in the portfolio. The formula for the standard deviation of the portfolio is explained here: https://en.wikipedia.org/wiki/Modern_portfolio_theory. The Efficient Frontier is the line drawn by the portfolios with the highest returns for each level of risk.

Let’s have a look at the code to run this Monte Carlo simulation and plot Markowitz Efficient Frontier. 

The First step is to import the libraries we will need: 

![](img/25.png)

We then move forward to pick our tickers and create the data frame with pandas_datareader: 

![](img/26.png)

Let’s now calculate returns and covariance of these returns as well as create empty list to store data from Monte Carlo simulation and pick the number of paths, in this case one million.

![](img/27.png)

We are now ready to run the Monte Carlo Simulation for one million different portfolios:

![](img/28.png)

And finally some code matplotlib to plot all portfolios in one color and the efficient frontier in another color:

![](img/29.png)

This is the resulting Graph:

![](img/30.png)

This graph shows all the portfolios resulting from the one million randomly generated combinations of weights for our four stocks. For example we can see that there is a very large number of portfolios that will exhibit a risk of 25% but expected returns for these portfolios will range from 21% to 29%. The portfolio with 29% expected return for a level of risk of 25% is located on the white line along with every other portfolio that has the highest expect return for each given level of risk. 


