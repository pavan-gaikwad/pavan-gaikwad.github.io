---
layout: post
title:  "ML AI basic terminologies"
date:   2023-03-01 21:48:43 +0530
categories: ml, ai, notes
---

Philosophically, ML changes the way you think about problems - you go from logic i.e. figuring out the details of how things should be done - to observations and experiments.

For example, instead of programming the computer to play chess by telling it how to behave for every possible move of the opponent - you feed the computer with data about chess moves from previously recorded games and let it learn how to play to win. If this sounds too weird, hold the thought we will trust the process to help us really understand how this works.

It moves programming from a logical space to a natural science of observations and experiments.

It would be extremely hard to program a computer to play chess and win against a human for every possible move on the chessboard. ML helps us achieve this.

So ML helps programmers do three things:

1. Reduce time spent programming (example above)
    
2. Customize and scale your products (social media feeds)
    
3. Solve seemingly “unprogrammable” problems (face detection, etc.)
    

---

## Basic Terminologies

Supervised ML systems learn how to combine input to produce useful predictions on never-before-seen data.

- **Label**: the variable we are predicting (For the email spam problem we would label the input emails as “spam”, “not spam”)
    
- **Feature**: input variables that describe our data. We extract them from the data (keywords in the email, header info, sender info, etc.)
    
- **Example**: One piece of data that can be labelled or unlabeled.
    
- **Model**: A mathematical construct that does the predicting (we will understand this later).
    
    - **Training** a model means creating or **learning** the model. That is, you show the model labelled examples and enable the model to gradually learn the relationships between features and labels.
        
    - **Inference** means applying the trained model to unlabeled examples to see what it predicts.
        
    - A **regression model** predicts continuous values. For example, regression models make predictions that answer questions like the following:
        
        - What is the value of a house in California?
            
        - What is the probability that a user will click on this ad?
            
    - A **Classification model** predicts discrete values. For example, classification models make predictions that answer questions like the following:
        
        - Is a given email message spam or not spam?
            
        - Is this an image of a dog, a cat, or a hamster?
            

---

## Linear Regression

In the terminologies section, we saw that a Regression model is a mathematical construct that predicts continuous values.

Linear regression analysis is used to predict the value of a variable based on the value of another variable.

**Dependent Variable**: the variable you want to predict

**Independent Variable**: variable you are using to predict the other variable's value

Linear regression tries to find a linear trendline that describes the relationship between the independent and dependent variables.

A linear relationship is represented by a linear equation.

The linear equation has the following general form:

y = mx + c

where y is the dependent variable, m is the slope of the line, x is the independent variable, and c is the y-intercept.

We got an idea, now let’s now deep dive into Linear Regression.