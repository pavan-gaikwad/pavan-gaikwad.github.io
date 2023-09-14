---
layout: post
title:  "Lakes and Rocks - Why it makes sense to have smaller releases?"
date:   2023-02-10 21:48:43 +0530
categories: devops
---
**In a DevOps implementation we usually assume that we have to ship smaller releases, frequently. I sometimes wonder if this is a good idea, does lean have an explanation?**

Lean led me to this idea of “Lake and Rocks” - when you reduce the water level i.e. _batch size_, the hidden rocks i.e. _the waste_ becomes visible.

Let’s say you have a process of shipping a release once every month. It is likely that your process has inflated itself to match the timeline. Refer [Parkinson’s Second Law](https://en.wikipedia.org/wiki/Parkinson%27s_law).

Now let’s say decide to ship a release every week, immediately there would be a hundred different things that would make it impossible to ship in a week. Your constraints become visible. You analyse these and work on fixing these - and hopefully come up with a leaner process that helps you ship in a week.

Then you decide to ship once a day and repeat the process.

**That makes sense, but I have a feeling this will slow down the whole thing initially.**

Yep, that is expected. The short term effect of this is the opposite of what you desire. But that is the key, you have to commit to it and find ways to improve the process.

**So how do you convince people around you that this needs to be done?**

It’s useful to look at this as a top-down initiative. Usually, you would need buy-in from the highest level and then educate people on lean principles.

Having said that, it should be possible to display the benefits. Theoretically you could present the obvious benefits. Practically too, if you are managing multiple services, then you can start with one where you have the least friction and start improving that.

Work towards that buy-in and educating people. Every organisation would do this differently. This could sound boring, but boring is the way to go.

**Makes sense. It always helps to lead with data. Plus I believe this is good for the business.**

Of course. Through the leaner process and faster shipping cycles, you are shortening the feedback loop from the users. Small changes are also easier to fix or improve.

Overall, business becomes capable of responding to market feedback fast.

Plus, there is operational efficiency that you achieve. Automation is obviously going to be the key for shorter release cycles - so there is less manual effort and manual errors. This improves the stability of the system.

**Summary:**

When you decide to work in smaller batches, the transaction costs of the old process becomes unacceptable - this leads to improvements.