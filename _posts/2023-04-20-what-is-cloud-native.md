---
layout: post
title:  "What is cloud native even?"
date:   2023-04-20 21:48:43 +0530
categories: ml, ai, notes
---
We all have heard this term “cloud native” everyday for years now, but lately I have been wondering what cloud-native really means? Everyone I spoke to had an overlapping but different model about what they thought cloud native means. For some its serverless, for some its kubernetes and for some others its just applications built with managed services exclusively.

While all of these are correct, I wanted to get to a definition. So of course the first place to look at was CNCF.

Here is what the [CNCF definition of cloud native](https://github.com/cncf/toc/blob/main/DEFINITION.md#cncf-cloud-native-definition-v10) is:

> Cloud native technologies empower organizations to build and run scalable applications in modern, dynamic environments such as public, private, and hybrid clouds. Containers, service meshes, microservices, immutable infrastructure, and declarative APIs exemplify this approach.
> 
> These techniques enable loosely coupled systems that are resilient, manageable, and observable. Combined with robust automation, they allow engineers to make high-impact changes frequently and predictably with minimal toil.
> 
> The Cloud Native Computing Foundation seeks to drive adoption of this paradigm by fostering and sustaining an ecosystem of open source, vendor-neutral projects. We democratize state-of-the-art patterns to make these innovations accessible for everyone.

That is quite what we imagine cloud native would be. Although it still does not define what cloud native is. I think the reason is that we just don’t know. With time we will keep updating the definition to include all the innovation happening in this space.

### So what could cloud native mean?

Let’s start with “cloud”. Cloud usually means a system that allows users to get access to computation on-demand and allows them to pay only for what they use. It can be either “Infrastructure as a Service” or “Platform as a Service” or eventually “X as a service”.

Native usually means “origin”.

Combining these ideas, cloud native could mean applications and services that are born in the cloud. In a scenario where developers are writing code in an “IDE as a Service” platform, testing it on “QA as a service” platform - for browsers we already have “Browsers as a service” which let us write tests and run them on the cloud.

I have personally tried “IDE as a service” platforms and they usually fall short because of the latency. Its usually too slow and you miss running an IDE on your own machine.

But what if how we write programs changes in a way where latency and unreliable networks are not a deal-breaker?

### Could AI finally make our applications cloud native?

AI is of course changing the way we program and its getting better every day. I have personally used both GitHub co-pilot and ChatGPT to write code and it is clear that the productivity of programmers is going to increase massively.

So the question is, will we eventually reach a point where we can prompt our way to a fully functional application? Only time can tell, but I think we are getting there. There are always obvious exceptions, but if you need an app that is mainly CRUD, that is going to easier to build with prompts.

So your IDE essentially changes from a tool where you write code to a tool where you prompt an AI and review what code is being written - and THIS could be done on cloud.

So imagine a future where you prompt an AI to build an application one step at a time. It writes code required to implement what you tell it to and runs it for you to test. If something does not work, you modify your prompts until it works.

This could also spawn new programming languages, interfaces and new generation of programmers.

I would explore this more until I see clear answers - and share what I find. Have a good day!
