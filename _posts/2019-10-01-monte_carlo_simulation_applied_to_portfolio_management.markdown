---
layout: post
title:      "Monte Carlo Simulation applied to Portfolio Management"
date:       2019-10-01 21:46:32 +0000
permalink:  monte_carlo_simulation_applied_to_portfolio_management
---




Monte Carlo simulations perform risk analysis by simulating models of possible outcomes according to a chosen probability distribution for a parameter that has an inherent uncertainty. To get a basic understating of how it works we can use a simple example and calculate the area of a circle inside a square with a binary outcome experiment. Let say that we don’t know the value of Pi and want to calculate the area of a circle of diameter of one. We can draw a square around that circle and start randomly plotting dots inside that square. In this case we would be following a uniform distribution for the coordinates of the dots we are plotting. If the dot falls inside the circle we will label it a success and at the end we will estimate the area of the circle by dividing the number of dots inside the square by the total number of dots plotted. 

As we will see in the illustration below, the number of dots plotted is crucial to obtaining an accurate result. If we don’t plot enough dots the value is likely to be far from the actual value but with a large number of random values it appears very likely that we will get a number very close to the right answer. Python allows us to generate more than one hundred thousand outcomes in a significantly short period of time which makes it a powerful tool to run Monte Carlo simulations. By using the formula A = πr^2 the area of a circle with a diameter of one is approximately 0.785. Let’s use Python to code the experiment and see how close to this value we get with different numbers of dots or different number of paths to use Monte Carlo terminology. <b>
All we are going to do is go through a loop of ‘n’ number of paths and for each iteration we will generate two random values between -0.5 and 0.5 because our circle is centered on the origin. The first of this values will be the x axis value for our dot and the second one will be the y axis value. Using this coordinates we calculate the Euclidian distance of the dot to the origin. If the distance is inferior or equal to 0.5, our dot is in the circle, otherwise it is outside. Finally we divide the number of dots inside the circle by ‘n’ to calculate the area. The following few lines of code are enough to run the entire experiment. <b>
All we are going to do is go through a loop of ‘n’ number of paths and for each iteration we will generate two random values between -0.5 and 0.5 because our circle is centered on the origin. The first of this values will be the x axis value for our dot and the second one will be the y axis value. Using this coordinates we calculate the Euclidian distance of the dot to the origin. If the distance is inferior or equal to 0.5, our dot is in the circle, otherwise it is outside. Finally we divide the number of dots inside the circle by ‘n’ to calculate the area. The following few lines of code are enough to run the entire experiment. 

![](img/23.png)


