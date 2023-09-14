---
layout: post
title:  "Feature Engineering - Intro and Basic terms"
date:   2023-04-07 21:48:43 +0530
categories: ml, ai, notes
---
Some 70% of the time of a machine learning engineer is spent on cleaning data and feature engineering. So this thing deserves a lot of attention.

Hence I have decided to dive deep into this topic.

## What is feature engineering?

Before we start getting into Feature engineering, it is important to understand what “data” and “models” are.

##### Data

Data relates to the quantification of a real-world phenomenon. How cold is the weather outside? How many runs did the batsman score? What is the BPM of the song?

  
Each such data point (“example”) provides a window to one aspect of the real world. You cannot paint a full picture with just data points, usually.

  
Also, this data might have inaccuracies because of many reasons - including errors by observers.

##### Models

Models help us make sense of the data. They help us answer specific questions. For e.g. Should I wear a sweater today?

A model can take in information about your location, the temperature data at that location, your preferences, etc. and give you a specific answer.

What are models exactly?  
Models are simply mathematical equations.

Now the immediate next question is - does that mean all data that is fed into the model should be numeric?

Yes. Text data, image data - everything should be converted into a numerical representation to be able to use for machine learning purposes. And that is where feature engineering comes in.

##### Feature

A feature is a numeric representation of data.

But how do we actually convert all of this data into features?

### Feature engineering for Text data

While analysing Text we need to have some goals in mind - w.r.t. what we wish to achieve with the given Text.

  
If you are analyzing a non-fiction book for creating a summary of it, you might want to extract unique ideas and their descriptions. Then you might want to extract the relationships between these ideas.

  
For a fiction book, you might want to extract the characters, the environment, important events, etc.

This is extremely subjective.

##### Bag of words

Let’s first see what a vector is: A vector is just a collection of numbers.

The Vocabulary is a set of all words in the text data. The way you create this vocabulary is by taking a list of all the unique words in the text data and assigning each number.

Then for each document being analyzed, you take a count of occurrences of each word in the document. The words from the vocabulary that do not occur in the document have a count of zero.

This way each document is converted into a vector which represents how many times a word occurs in the document.

It’s better we see an example of this. Here's an implementation from my Github repo.

#### Python Code to Implement Bag Of Words

[**_GitHub repo with the code_**](https://github.com/pavan-gaikwad/N-DAYS-OF-ML-AI/blob/main/bag_of_words.ipynb)

# Problem statement[¶](#Problem-statement)

We are learning feature engineering and we are looking at how to extract features from Text data. So the problem at hand is that how do we convert text data into numerical data so as to run them through ML algorithms. One way to do this is by using "Bag of words" method.

We start off by importing CountVectorizer from sklearn python library.

In [ ]:

```
from sklearn.feature_extraction.text import CountVectorizer
```

We then pass the text data that we want to vectorize. Our goal is to convert these two sentences into a numerical representation.

In [ ]:

```
text_data = ["We will use short sentences to illustrate the concepts.",
             "Once we get the concept of bag of words, we can move on."]
```

The CountVectorizer function is a class in the sklearn library that is used to create a bag of words representation of text data. It does this by taking a corpus of text data and creating a vocabulary of words from it.

In [ ]:

```
vectorizer = CountVectorizer()
```

From the CountVectorizer class we call the fit_tranform function that converts the text data into a bag of words vectors.

In [ ]:

```
bag_of_words = vectorizer.fit_transform(text_data)
```

We can now see the full vocabulary. Here the vocabulary represents all the words we have in our text data.

The way the vocabulary is created is by taking each unique word from our text data and assigning it a number.

The result can be seen below.

In [ ]:

```
print("Vocabulary:", vectorizer.vocabulary_)
```

```
Vocabulary: {'we': 15, 'will': 16, 'use': 14, 'short': 11, 'sentences': 10, 'to': 13, 'illustrate': 5, 'the': 12, 'concepts': 3, 'once': 9, 'get': 4, 'concept': 2, 'of': 7, 'bag': 0, 'words': 17, 'can': 1, 'move': 6, 'on': 8}
```

Finally here is the "bag of words" representation of our text data.

We go through each sentence in our text data. For each word in the sentence we look up the position in the vocabulary and increment that position.

This way for each sentence we get a vector representation. In this representation we can tell how many times any word occurs in our sentences.

In [ ]:

```
print("Bag of words:", bag_of_words.toarray())
```

```
Bag of words: [[0 0 0 1 0 1 0 0 0 0 1 1 1 1 1 1 1 0]
 [1 1 1 0 1 0 1 2 1 1 0 0 1 0 0 2 0 1]]
```

In the bag of words method, you simply count the number of occurrences of every word in a document.

It is a flat vector i.e. there is no hierarchy, it is simply a count of each word in the document.

## Intuition for Bag Of Words

The intuition here is to imagine the sentences in n-dimensional space, where n is the number of words in the vocabulary.

In an n-dimensional bag of words representation, vectors that are closer to each other typically have more similar meanings.

The closer two vectors are to each other, the more similar their values are, which typically indicates that the texts they represent contain more of the same words.

For example (from the internet), consider the following two sentences:

- "The quick brown fox jumped over the lazy dog"
    
- "The dog was not amused by the fox's antics"
    

If we create a bag of words representation of these sentences using the words "the," "dog," "fox," and "quick" as the vocabulary, the vectors for each sentence would be as follows:

- "The quick brown fox jumped over the lazy dog": [2, 1, 1, 1]
    
- "The dog was not amused by the fox's antics": [1, 1, 1, 0]
    

These vectors are closer to each other than they are to vectors representing sentences that contain different words, such as:

- "The quick brown rabbit jumped over the lazy cat": [2, 0, 0, 1]
    

This indicates that the first two sentences are more similar to each other in terms of the words they contain, and thus have more similar meanings. In general, vectors that are closer to each other in an n-dimensional bag of words representation are more likely to represent texts that have similar meanings.