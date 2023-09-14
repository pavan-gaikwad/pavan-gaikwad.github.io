---
layout: post
title:  "Beginner's guide to chatGPT and ML"
date:   2023-05-30 21:48:43 +0530
categories: ml, ai, notes
---
Please note: I have taken the liberty to simplify topics and provide analogies. This document is not for you if you already know what neural networks are or how machine learning works.

# What is chatGPT?

ChatGPT is an application which allows you to have a textual conversation with an **ML** **model**.

We are going to break down this sentence so we understand the terms mentioned.

### What is ML?

ML stands for machine learning. A domain within computer science that deals with making “software that learns”.

### What does it mean? Software learns?

Yes. See, before the digital computer, every machine was built to do a specific task. A printer would print, a camera would take pictures, phones helped with long-distance communication, calculators calculated, watches showed time, etc.  
Then we invented digital computers.  
Now the same computer can print, take pictures, calculate, show time, make phone calls, send emails, etc.  
**The difference is the software.**  
Digital computers have the same hardware but thanks to the software running on them, they are capable of performing diverse tasks.

### Now let’s talk about software.

Software is a set of instructions that developers write to make the computer do something.  

The computer runs on electricity. That way it is no different than your ceiling fan. When you pass electricity to your fan, it starts rotating.

  
Same way, the computer is a system that when you pass electricity to it, “computes” - it calculates. It computes “instructions”.

From here, we can go into a bottomless rabbit hole. But for the sake of this article, we will stop at the fact that a **digital computer executes instructions when electricity is passed to it - these instructions are provided by human developers.**

### But wait, that means computers are limited by the human ability to instruct them? Maybe we are limiting computers to our ability to instruct them. How will computers become smarter than us then?

Great question. Imagine writing a program to identify what objects are in a photo.  
Can you imagine writing a set of instructions to identify what the photo consists of?  
Think about it.  
“If there is a brownish rectangle and there is a green circle thing on top, it is a tree. But wait, it’s not always circlish, sometimes it can be long lines also in the case of coconut trees, but then there is the autumn, where there are no leaves”

It is impossible for a human to program every detail.

Now think about how you (your brain) identify a tree?  
If I show you a tree you can identify it. Any tree. It could be a tree you have never seen before and you will still understand it’s a tree once you see it.  
How does our brain do it? Maybe because you have seen countless trees since you were born and your brain has learnt something un-describable that enables you to identify any tree on the planet.

**Your brain has a “general mental model” of how a tree looks.**

Now imagine if software could learn this way. We could make it learn things that are almost impossible to program - like “image detection”.

### Enter machine learning. Software that can learn.

Intelligent software does not depend only on the instructions from the developers. This software looks at a large amount of data and learns patterns independently. It learns to identify a tree by looking at a large number of trees.

We will definitely not get into the details but one way to do it would be this:

> _Imagine a “teacher” and a “student” software._
> 
> _A “student” software is provided a large number of photos and asked to guess if its a tree._
> 
> _The “teacher” software knows whether the image is of a tree or not._
> 
> _The teacher software then shows the student software an image and asks if its an image of a tree._
> 
> _If the student software’s answer is accurate, then it is rewarded. If the answer is wrong, the student is “punished” - tuned and made to try again._

This tuning continues until the software largely guesses correctly.

**The student software now has a mental model of how a tree looks.**

Once this process is completed, the student software is ready to see any new image and tell you if it’s a tree with some accuracy.

Disclaimer: it is essential to note that modern image detection systems, such as convolutional neural networks (CNNs), are far more complex and sophisticated than the simple description provided in the article.

### But look, not everything I have learned has been taught to me. I am sure if nobody “taught” me what a tree was, I would still be able to identify one.

Of course.

### Supervised and Unsupervised learning.

The example we saw above is related to supervised learning. Why? Because the “teacher” software supervises and provides feedback.

But not everything learned is not “taught”. In machine learning too, the software can learn without being taught.

Imagine you are a detective, and you have a bunch of mysterious pictures in front of you. Your task is to find any hidden patterns or similarities among these pictures without anyone telling you what's in each picture. This is what unsupervised learning is about—it's like being a detective with no labels or hints.

In unsupervised learning, you take your “student” software and show it lots of pictures. Instead of telling the software what's in each picture, you let them figure it out on their own. They start to look for common elements, like similar shapes or colours, and group similar pictures together.

The software keeps repeating this process, rearranging the pictures into different groups, trying to find better patterns each time. It's like organizing a messy collection of photos into different albums based on what they think looks similar.

After a while, the software becomes pretty good at spotting patterns. It might create an album of pictures showing dogs, another album with cars, and so on, even though you never told it what's in each picture.

Now, if you show them a new picture that they haven't seen before, they can make a guess about what it might be. They'll compare it with the patterns they've learned from all the other pictures and say, "Hmm, this new picture looks a lot like the ones in the 'dogs' album, so it's probably a dog!"

That's how unsupervised learning works. Broadly.  

### Models. In AI, we keep hearing of models, what exactly are these models?

Models are mathematical equations. That’s it. It can be a simple equation or an extremely complex one. An equation provided by programmers or an equation that the computer comes up on its own - “learning”.

### OK. Now let’s move to how chatGPT works?

A good way to understand ChatGPT is to start with what its name means and then break it down.

**What does a GPT stand for?**

> **GPT stands for Generative Pre-Trained Transformer.**

**Generative** - The model generates data (text, images, videos, audio, etc.)  
**Transformer** - This is the “student software” we talked about earlier. It mimics the “network” of Neurons in the organic brain. Transformers and neural networks are inspired by some aspects of how the brain works - it's important to understand that Transformers are a specific type of neural network architecture designed for tasks like processing natural languages.

In the case of GPT - the “student software” or the “Transformer based neural network”, is trained on Text and generates Text.

The way the model works is, it will generate the next token (character, word, sentence) based on what is passed to it as input. The model simply completes your sentences.

So let’s say you pass this input to the model: “I want to” - It could respond with “I want to break free”.

### But how does it know how to complete my sentences? Does it have all the knowledge in the world?!

Actually no. The model simply completes the sentence by what it thinks are the most likely words to follow. What it thinks is likely, depends on the data the “teacher” software passed to it while “training” it.

You could call this knowledge.

But the point to take away is this.

The output that you get out of ChatGPT (the model, ignore the plugins) - is often what it thinks is more likely than what it thinks is accurate.

The model's output is based on probabilities and the patterns it has learned from the training data, so it typically generates what it believes to be the most probable continuation of the input. In many cases, this aligns with accuracy, but it is not guaranteed to be correct in all situations.

### Let’s talk about an example to illustrate this.

Try asking chatGPT for the plot of a movie you know. You will find it will get most of it right but then it will “hallucinate” some details.

Now, this example is for anyone who has watched the movie “Hum Saath Saath hai”. I asked ChatGPT to explain to me the plot of this movie. Most of the things it responded with were correct. But it also came up with this:

`The family is deeply rooted in traditional Indian values and believes in the significance of togetherness. They live harmoniously and happily, sharing a strong bond with each other. However, their happiness is threatened when their distant relatives, Mamta's brother-in-law, Anurag (Shakti Kapoor), and his wife, Choti Bahu (Sadashiv Amrapurkar), plot to take advantage of the family's wealth and create misunderstandings among them.`

`The story takes a dramatic turn when Mamta is accused of hiding her wealth and distributing it unfairly among her children. This accusation causes a rift in the family, leading to a legal battle and emotional turmoil. Amidst these challenging circumstances, the family's unity and love are put to the test.`

  
This is obviously incorrect. As per ChatGPT, Shakti Kapoor’s character is the villain - which is wrong.

But why do you think it responded this way? Was it because it was more likely that Shakti Kapoor was the villain based on his general filmography? Just more likely.

### What about the “chat” in chatGPT?

The chat bit is another layer of training on top of the GPT model. This gives it the ability to respond to queries as opposed to just completing sentences.

There are again, many techniques to do this, but we’ll look at RHLF (Reinforcement Learning from Human Feedback). In this human beings are in a loop and they train the model using a pre-made “QnA” set. They ask questions, rate answers and “train” the model further. Once trained this way, the model is ready to respond to questions instead of simply generating text.

So that wraps it up. This is a very simplified view of the ML domain and I hope it helps you in some way.