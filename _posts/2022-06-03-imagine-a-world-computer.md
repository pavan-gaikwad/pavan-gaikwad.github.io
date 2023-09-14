---
layout: post
title:  "Imagine a world computer"
date:   2022-06-03 21:48:43 +0530
categories: web3, blockchain
---

…well, you log in to this computer and you can see all the apps that everyone using the computer has ever installed. You see all the data that was ever saved by all users.

You can save your own data on this computer.

You can use other people’s apps - to the extent they allow you to.

You can build and install your own apps and allow others to use them to the extent you want them to.

Everything that you save on the computer is linked to your identity and is permanent. Whatever you save on this computer cannot be deleted or modified. Including the data that you write and the apps that you install.

Basically, one public computer where all the data is saved and no modifications are allowed.

### But WHY? Who would use such a computer? You can only upload data and apps but you cannot modify or delete anything? Seems pretty useless.

It can be used to save information that you wish to keep unmodified. It’s great for recording facts. Your test scores, your monetary transactions, the real estate you own, scores from your football matches, studies on the harmful effects of sugar, etc. Facts that you want to preserve and don’t want to be modified.

### Isn’t this already happening? I am sure nobody is tampering with the match scores and my monetary transactions are recorded just fine.

If we build this computer, then all the facts can be recorded on this computer and we will not need to trust other people and institutions with the information. All the trust can be baked into this computer thereby making the system transparent.

They can in fact leverage the computer to their job in a transparent and efficient manner. In case the system is broken or corrupt, users can opt out of it and move to our world computer as a store of trust. Right now, you do not have an option to opt-out.

### That’s a powerful idea, but that means we have to trust the people who build the computer, the operating system, the code and the hardware. So we are just shifting trust?

Yes, I guess. We will have to build mechanisms through which we can trust the group of people building this computer.

### But isn’t that exactly what we do now? We build systems of governance to manage trust between people and the institutions.

The concern is the custodians of the governance are also people. Here the governance is managed by economic incentives and an unmodifiable computer code. Power does not lie with a single person or a small group of people, it is distributed more widely and rules are written down, unmodifiable and impartial. Like democracy.

### Seems flaky.

It is. Code can have bugs and we cannot possibly cover all of society’s governance in code. There will be edge cases and edge cases are where the governments come in. This is not an institution-dismantling solution. Though it can be used to make institutions efficient.

We can definitely apply this computer in narrow domains like say, property rights, banking, music royalties, ticketing, elections, etc. where the rules are well-defined and simpler.

### OK, there is a lot to process with regards to the “why”, I am still not sure. But let’s move ahead. How would you build a computer like this?

One option is to obviously get a giant space and install a very powerful computer there - one you can expand in an unlimited manner. Then you can let everyone have access to it via. the internet. Remote access to the computer for everyone.

### But you said this is a special computer, everything saved on this computer cannot be modified or deleted. If we have a single computer then what if a few people barge in with guns and burn the whole thing down? They could delete or modify our facts too.

Yea that would be terrible. That is not something we want. We cannot put it in one place then, maybe we can put it in multiple places so there is no single point of failure.

### OK, multiple computers make sense. But won’t this require all computers to be in the exact same state? We don’t want one person to log in to one computer to see one set of facts and someone else logging into another computer to see something else. How do we achieve this?

Right. So each of these multiple computers will have to be exact copies of each other. They will all have to have the same data and apps installed. Anything saved on one computer should be saved on all other computers. This is going to be a challenge. We need a mechanism to keep data in all computers in sync.

### Plus, if anyone can use this computer then people will just use it all the time and we will surely run out of disk or memory or CPU or whatever.

Hmm. We will need a mechanism by which we can constrain the use of this computer so people don’t misuse it.

### Before we solve these problems, how do we set this up? Who would spend money and time to set this thing up? Why would they do it?

We need to incentivise some people to set up these computers. These are going to be expensive computers to buy and run so they will need to be compensated financially.

### What if we collected rent from people who use this computer and paid it to people who set up the computers?

That is a great idea! This helps compensate people hosting these computers while preventing misuse by users because they will have to pay to use the computer.

> So far - we have a world computer which is actually many computers connected together and are exactly alike (kept in sync). Anyone can use and anyone can set up a computer. People who use the computer pay the people who run the computers. So now we have a market for recording facts.

We are still not sure why we are building this, but this seems like fun.

### Yep. Let’s look at the sync problem. Keeping data synced between all computers across the globe is going to be problematic.

Let’s see. For this computer, we do not modify or delete data once written - so we have to ensure that all data that is saved on any computer is saved on every other computer at the same time.

This means we can only save one thing at a time. Save data → Sync all computers → Save the next piece of data.

This also means that data has to be small, text data. Imagine saving large images or video files this way. It will take a very very long time before such a large file is synced across all computers.

### Won’t that make this computer very slow? In fact, the more people host a computer the slower it will get because there will be more computers to sync to.

Yes. But that is the best way we know how to sync reliably. More computers mean that the computer system is resilient but it makes it slower. It is just how it is now.

### So what if I want to save something urgently?

Pay more fees. The higher your fees are the faster will your data be saved. After all, the people running the computers do it for the fees.

### You mean, I have to pay for every save?

Yes.

### Why not a monthly or an annual subscription to use the computer?

The demand to use the computer is going to vary and saving data is going to be expensive. The fees will have to be a function of the demand at any time. So higher the demand to record facts at a given time, the higher will be the fees.

There will be surge fees for using compute.

The demand and supply are extremely unpredictable. Remember, these computers are run by random people from any location they want. So not all of them will be online at all times. This means the time to sync data is going to vary. Demand is naturally going to vary. In case of high demand, the network is going to have a lot of pending saves so the fees to save are going to rise - there could even be bidding for faster saves.

### I am starting to think about videos - imagine saving a video fact and it syncs to many hundreds of computers across the world. It is going to take a loooonggg time.

That is why we cannot store large files on this computer. Only simple text can be saved. Imagine a lot of users saving images. It will slow down the computer due to the sync process, increase the bottleneck and demand will increase thereby increasing prices greatly. We can only do text data I think.

### Only text information can be saved? This is a big limitation. How can this be useful for anything?

What we could do as a workaround is to save the representation of large data instead of the data itself. So let’s say you bought an album from your favourite artist, you definitely cannot save the large audio files on this computer, but you can save the name of the album and your identity on the computer in text format. A single line saying “X person bought an album from Y artist for Z amount”.

### This looks like a transaction.

It does. Everything can be represented as a transaction on the internet. In fact, programmers call all “data save” requests part of a transaction.

### So if we are only recording transactions on this computer, why not use a Ledger? Ledgers have been used for centuries to record transactions. Pretty sure they will be the most efficient way to save data and will provide us with some capabilities to trace facts.

We should use a Ledger. Ledger as a data store will be a good idea. A Ledger will also save the time for the transaction so we can model time into our data. This will be useful to line up facts on a timeline - just like in the real world. This sounds great!

> So we have a Ledger that is run by multiple people and is always in sync. It records transactions in a text format and records time for each transaction. Let’s call it a **Distributed Time-Stamped Ledger**.

### So we will need to turn our computer into a special-purpose computer which will behave like a Ledger.

I have some ideas there, we will come to that.

### Let’s call it a day. We still have a lot of things to figure out next time.