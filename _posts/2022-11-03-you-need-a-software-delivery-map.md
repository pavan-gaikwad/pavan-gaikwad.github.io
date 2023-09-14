---
layout: post
title:  "You need a software delivery map"
date:   2022-11-03 21:48:43 +0530
categories: devops
---
> Value Stream Mapping is an immensely helpful tool while planning your DevOps/SRE/Automation implementation. I have used this for large and small processes with great results. Introducing some ideas with this post that we will build up on in the future.

---

**Tell me what tech I need to implement DevOps.**

Wait. Before you even think about the technologies, you need to understand what it is that you want to improve and why.

**It's pretty clear, that I want to improve the quality and speed of delivering features to my customers.**

That is the goal, yes. What you need to do, in what order, to get to this goal is equally important. You don't want to spend your resources improving areas that do not add maximum improvement to your system.

**Improvement? I thought we were going to implement DevOps, which means we start from scratch. My current system is hopeless.**

But it does work, right? It is tempting to start all over again, and honestly, it is a lot more fun. But. Continuous improvement is an effective idea in the long run. Your current system got you to where you are, your processes are built around them and your people are used to it. To replace the entire thing is going to be hard. The last thing you want is your people rejecting your improvements because they are too abrupt. A continuous, incremental improvement done through rapid iterations is a good idea.

**But aren't industry best practices defined? Can't we just adopt them for a great new system?**

That's the tricky part. Think about if your organization is exactly identical to every other organization. Is it even similar to every other organization in your industry? Each organization does things differently and has a different value proposition with unique features. If your organisation indeed do things differently, you'll have different processes, different organisational structure, and different aspects of the business that you value more than the others - you get the point.

You need to identify what works _specifically_ for your business and what does not. Once you understand this, you can look at best practices and adopt only those which make sense for your business and skip others. Everything comes at a cost so we need to be careful here.

**Alright, even if I take your word for it, how do I know what to improve? I have tons of ideas already. I have thoughts about which tools to use, which processes to automate, etc.**

This is extremely important. We have tons of ideas so it becomes crucial that we have a mechanism to prioritize them. This mechanism should be objective to a large extent, easily understood by everyone and should be data-informed as much as possible.

**How to build such a mechanism?**

One way to do it is using _Value Stream Mapping_. I'll leave a link[1](#footnote-1) at the bottom for you to get into the details and to get a good understanding of this tool. The basic idea though is that you plot your process visually and then quantify the time taken at each stage or anything else really. Just read through it.

Definition: _Value stream is a series of steps that occur to provide the product or service that their customers want or need._

**How do I measure? I do not have any numbers right now that can tell me how much time is being spent where.**

That is where everyone starts. You'll have to spend some time digging into the details. Look at your Jenkins jobs and see if you can get data from there. Get the intuition of people who work on these systems first-hand. If these are not possible, sit down and do the job. Do it until you are able to plot the Value Stream for your process and have enough details to start with.

**What else to measure apart from time?**

Time is just one thing. You can measure anything that is important to you. Let's say you are solving for errors - your people are frustrated that there are too many errors in the system. For solving this, you can measure the error rate at each stage of your Value Stream. You could also put cost - which areas are more expensive to run than the others.

You can pretty much put any parameter that is of interest to you. This map is exactly what it is, a map. It provides direction, ways to prioritize and alignment. This will help you build a roadmap to which you can align everyone.

**_Start Value Stream Mapping your unique software delivery process._**