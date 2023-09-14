---
layout: post
title:  "Pay as you go chatGPT"
date:   2023-05-26 21:48:43 +0530
categories: ml, ai, notes
---
_(If enough people are interested, I will do a detailed explainer for non-programmers. Currently, this is meant for programmers who are comfortable with React, CLI and GIT)_

The current cost of a ChatGPT subscription in India is USD 23 (with taxes). Whether that cost is steep depends on you really, but I thought it would be a good idea to see if I really do use USD 23 worth of ChatGPT each month.

Of course, I can use the free version but I also want access to GPT4 and a faster, reliable response time. Plus with Bard, do I really need to? Really? Maybe?

As an experiment, I put together a barebones React chat app to use ChatGPT via. the OpenAI API. With my usage, the cost per month is around USD 3. That is quite a difference.

Of course, a lot depends on which models you use and the token length, but still.

Here’s a screenshot of how the app looks (it is pretty barebones)

[

![](https://substackcdn.com/image/fetch/w_1456,c_limit,f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fafe9e4a1-da1f-4f94-8d19-181bf8245f34_2312x1414.png)



](https://substackcdn.com/image/fetch/f_auto,q_auto:good,fl_progressive:steep/https%3A%2F%2Fsubstack-post-media.s3.amazonaws.com%2Fpublic%2Fimages%2Fafe9e4a1-da1f-4f94-8d19-181bf8245f34_2312x1414.png)

## Installation instructions

#### Pre-Requisites:

- You will need an OpenAPI developer account and an API key. [Click here.](https://platform.openai.com/)
    
    - REMEMBER TO ADD A BILLING LIMIT TO YOUR ACCOUNT, YOU DO NOT WANT A LARGE BILL IN CASE API KEYS ARE SOMEHOW COMPROMISED
        
- NodeJS (Version v17.1.0)
    
- Knowledge of how to use CLI
    
- Free time
    
- The excitement of saving coffee money.
    

### Installation

- Download the code from [here](https://github.com/pavan-gaikwad/AIReach/archive/refs/heads/main.zip) OR “git clone” it if you know what that means.
    
- Open your CLI tool (CMD or Terminal)
    
- Navigate to the directory where you downloaded and extracted the code.
    
- Run the command “npm install” to install dependencies.
    
- Once this command finishes, run “npm run start”
    
- It should pop up a browser and start the app.
    
- The app will ask for your API key, put it.
    
- DO NOT SHARE YOUR API KEY WITH ANYONE OR ELSE YOU WILL PAY
    
- REMEMBER TO ADD BILLING LIMITS ON YOUR API ACCOUNT
    
- REMEMBER TO CHANGE API KEYS EVERY NOW AND THEN
    
- THIS APP DOES NOT SAVE YOUR API KEY. ON PAGE REFRESH IT WILL ASK YOU FOR THE KEY AGAIN.
    
- I NEED A DOSA