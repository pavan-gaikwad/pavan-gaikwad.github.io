---
layout: post
title:  "Intuition for linear regression"
date:   2023-03-03 21:48:43 +0530
categories: ml, ai, notes
---

Linear regression. Let’s break it down.
Regression, as we saw from the terminologies, means a mathematical model that predicts continuous values.
Linear means “arranged in or extending along a straight or a nearly straight line”. 

So let’s get the intuition going before we get into the details.


### Problem Statement
Let’s start with where we can use this. Let’s say you have data like this:
```
X = (0,10,20,30,40,50,60,70,80,90,100)
Y = (12,32,54,45,45,65,76,67,50,65,86)
```
![[Pasted image 20221201105411.png]]

Let’s say we want to predict what Y is for a when X = 110

#### Idea
The idea with linear regression is to fit a line through this data such that we can see where the pattern is headed. Once we have a line that fits well, we can use it to guess the next set of values.

How do we know if a line fits well? Of course, with our eyes we might be able to visualise a straight line that moves through this data and fits well - but how do we do this mathematically?

Here is where the idea of an error function or a loss function comes in.

A loss function quantifies how much the line has to compromise or how far it is from each point.

There are many loss functions (apparently, we are on day 3 and we trust the process :D) but the one we are using here is called a Mean Squared Error.

At this point lets see a line that fits through this data. We will get to how I got this later.

![[Pasted image 20221201112236.png]]

The error at each point in the chart can be denoted as $y-y'$ i.e. actual value of y for a given x minus the predicted value of y for the same x as per the straight line fit.

We then square this error - why? - we will get to it eventually.
So we now have $(y-y’)^2$

This is the squared error for one example x.

We have to optimise for the entire set of values so we calculate this squared error at each point and then we take a mean of these errors.

For a line where this mean squraed error is minimum is the line that is the best fit.

```
Mean Squared Error=\frac{1}{N}\Sigma_{i=1}^n (y_i-prediction(x_i))^2
```
Phew!


How do we find the minimum? By trying every possible line? Maybe. Or is there a better method to find it? We will look into this later.
For now, lets start running some code to solve our prediction problem statement.

---

We need to install some software.

- We’re going to use a Python library called “conda”. [Download](https://www.anaconda.com/products/distribution)
- Once conda is installed, run these commands from your CLI.
	- conda create -n ml_env python=3.8
	- conda activate ml_env
	- conda install matplotlib
	- conda install scikit-learn
	- conda install jupyter
- These commands would install all the required dependencies.
- Next we need a notebook to actually write some code and make predictions.
- To start the notebook run this command from your CLI:
	- jupyter notebook
- This should open a notebook in your browser.
- Go to “Files” tab > New > Python3
- At this point you will have a notebook open.
- Run these commands in the notebook one line at a time.
```
import numpy as np
import matplotlib.pyplot as pyplot
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error, r2_score
x_var = np.array([0,10,20,30,40,50,60,70,80,90,100])
y_var = np.array([12,32,54,45,45,65,76,67,50,65,86])
l_reg = LinearRegression()
x_var=x_var.reshape(-1,1)
l_reg.fit(x_var, y_var)
y_pred = l_reg.predict(x_var)
pyplot.xlabel("X")
pyplot.ylabel("Y")
pyplot.scatter(x_var, y_var)
pyplot.plot(x_var, y_pred, color="yellow")
pyplot.show()
print("Mean squared error: %.2f" % mean_squared_error(y_var, y_pred))
our_prediction = l_reg.predict([[110]])
print("Predicted value of y for x=110 is %f" % our_prediction)
```

Here is a screenshot of the output you would see.

![[Screenshot 2022-12-01 at 11.53.08 AM.png]]


---
So we have got a fair bit of intution about linear regression and how the error function works to find the best fit.

Next step is to now get deeper into Linear Regression and understand how the minimisation works.