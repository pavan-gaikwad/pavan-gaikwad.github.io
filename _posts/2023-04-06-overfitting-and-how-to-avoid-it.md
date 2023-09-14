---
layout: post
title:  "Overfitting and how to avoid it"
date:   2023-04-06 21:48:43 +0530
categories: ml, ai, notes
---
### Overfitting

Overfitting in machine learning occurs when a model is trained too well on the training data and doesn't generalize well to new, unseen data. This means that the model will perform well on the training data but cannot make accurate predictions on new data.

Now there are techniques you can use to avoid overfitting. One of which has to do with using validation sets.

### Training, Test and Validation sets

By now we know that we need data to train our models. We tweak our features and hyperparameters to find the optimal fit.

But if we use the whole data set to train the model, how do we then test how accurate our predictions are?

We could split the training set into two sets - Training Set and Test Set of data.

We could train our model on the training set and then test it on the test set to see how well it is doing. This approach has a problem though, if we keep doing these iterations - train on training data, tweak features and hyperparameters and test on test data - we could end up overfitting our model to work well on the test data.

When this happens, the model would be less accurate on any new data.

One way to avoid this is to use another split of data called the Validation Set.

So now we use the training data to train our model and we validate our results on the validation data set. Once we are satisfied with the results, we test our model with the test set.

This helps reduce the risk of overfitting our model to the test data.

#### How to split the data between training, test and validation set?

For one, the more data we have to train the model, the better.

There are several different ways to split the data, but a common approach is to use a 70/15/15 split, where 70% of the data is used for training, 15% is used for validation, and 15% is used for testing. This split ensures that there is enough data in each set to train and evaluate the model properly, without one set being too small to be meaningful.

This is a good time to refer to the basic assumptions of supervised learning.

#### Basic assumptions of supervised learning

- We derive examples independently and identically, at random from the data set.
    
- The data distribution is stationary i.e. it does not change over the time we are training and testing the model.
    
- We always draw our sets from the same data distribution. We don't suddenly start drawing data from a new set.
    

I've learned that in practice we sometimes violate these assumptions - will come to this later.