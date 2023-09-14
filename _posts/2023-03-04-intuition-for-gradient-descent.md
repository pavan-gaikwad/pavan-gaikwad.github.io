---
layout: post
title:  "Intuition for Gradient Descent"
date:   2023-03-04 21:48:43 +0530
categories: ml, ai, notes
---
Yesterday i learned about the linear regression model.

- So we have two sets of data - one dependent and one independent.
    
- We feed these variables into a linear regression algorithm and get a model that is a good fit for our data set. This model can be represented as [latex]y = b + wx[/latex]
    
- To find the optimum values of [latex]b[/latex] and [latex]w[/latex], we have to minimise the loss function.
    
- Error is the predicted value by our model minus the actual value for that example. [latex] (y_g - y) [/latex] where [latex]y_g[/latex] is the guess bu the model for a given example x.
    
- The loss function we used is called a Mean Squared Error function.
    
- We calculate this error for every data point and get a Mean of this error dataset to come to a value of Mean Squared Error.
    
- The place where Mean Squared Error is minimum, is a good fit.
    

Now this explanation is incomplete but useful to start off.

Moving on.

How do we actually minimise the loss function? Let's start with the visualisation of how a error square looks like.

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe737793c-233e-498e-b686-0632c2a261c3_640x480.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fe737793c-233e-498e-b686-0632c2a261c3_640x480.png)

Now, looking at it we know that the minimun error is in the middle. Woohoo! - BUT how do we derive this conclusion mathematically so we can use it to program our computer?

Phew! So that is where **Gradient Descent** comes into the picture.

### Gradient Descent

In the context of machine learning and optimization, **gradient descent** is an algorithm that is used to minimize a loss function.

Break it down - gradient refers to the partial derivatives of a function with respect to its input variables. In other words, it is a vector of the slopes of a multivariate function at a particular point.

Remember, we are taking a top-down approach. We just trust this is true and come back to this later.

So we will use Gradient Descent algorithm to find the model with the minimum loss.

#### Intuition for Gradient Descent

Lets say you were 2-dimensional and were standing on the curve above at some random location. For added drama, imagine it is pitch dark and you cannot see anything around you.

In this situation, how do you find the lowest point in the curve?

My guess is that you will feel the slope of the curve below your feet and then you will move slowly downwards. Great!

Now let's say you want to find the lowest point in the minimum time, in this case you would also have to find the optimal distance you travel for each downward step. Too slow and you take too long, too big a step and you might overshoot the minimum and go to the other side.

Those essentially are the two variables to be optimised for Gradient Descent.

1. Slope of the curve.
    
2. How large a step to take down the slope.
    

#### A little math

How do we find the slope of the curve?

To find the slope of a curve at a particular point, we can use the concept of a derivative. In calculus, the derivative of a function is a measure of how the function changes as its input values change. It is often denoted by the symbol [latex]f'(x)[/latex] or [latex]df/dx[/latex].

To find the slope of a curve at a specific point, you can take the derivative of the function that describes the curve at that point. The derivative will give you the slope of the tangent line to the curve at that point.

For example, consider the function [latex]y = x^2[/latex]. To find the slope of the curve [latex]y = x^2[/latex] at the point (3, 9), we can take the derivative of the function with respect to x. The derivative of [latex]y = x^2[/latex] is [latex]y' = 2x[/latex], so the slope of the curve [latex]y = x^2[/latex] at the point (3, 9) is 2 * 3 = 6.

In general, finding the slope of a curve at a specific point involves taking the derivative of the function that describes the curve and evaluating that derivative at the point in question. This can be a complex process, and it typically involves using calculus techniques such as the chain rule and implicit differentiation.