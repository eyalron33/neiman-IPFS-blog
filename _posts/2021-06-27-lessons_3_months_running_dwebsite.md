---
layout: post
title: Lessons learned from three months of running a decentralized website
category: SGO
date:   2021-06-27 00:00:33 +0100
comments: true
author: Neiman
description: What did we study from three months of running esteroids.eth?
tags:
    - Esteroids, ENS, IPFS, dWebsites
---
It’s been three months since we launched Esteroids Alpha.

Esteroids Alpha is a decentralized websites (dWebsites) explorer. We are now working on Esteroids Beta, which is going to be search engine for the decentralized web.

Here are some lessons we studied during this period.

<img style="width: 640px; border:1px solid #021a40;" src="{{ site.baseurl }}/resources/images/lessons-3-months-running-dwebsite/cover.png">


## People need a dWebsites explorer

The evidence speaks for itself.

- [Our Twitter](https://twitter.com/e_steroids) has 300 followers without any promotion.
- There are daily visitors coming to see the dWeb in [esteroids.eth](https://esteroids.eth.limo/#/), even though it still has many hiccups and a rough design (remember, it’s alpha!).
- Our submision to Hacker News got [33 upvotes and 41 comments](https://news.ycombinator.com/item?id=27551619#27552409). Little known fact: the original link was [this](https://twitter.com/e_steroids/status/1405914760017756164). It was later replaced by the mods to  [Introduction to dWebsites]({% post_url 2020-05-21-Introduction_to_Dwebsitse %}) post from Almonit blog. Ironically, I wrote both the Esteroids tweet and the Almonit article.

Besides, we talk to people, we get feedback, we see the appetite for a tool to discover the new decentralized web.

## People actually want a search engine for the decentralized web
While people may need a dWebsite browser, but they often tell us they want a search engine.

Why? guess a search engine is just conceived as a basic tool that thenew Internet needs.

But no one knows which kind of search engine the decentralized web needs! A google clone? Naaaa, we’re not here to clone the old web.

## Esteroids Beta version is going to be a search engine for the decentralized web

That’s more an announcement than a lesson really. We see people want a search engine, so we’re gonna give them one soon.

The search engine will be created in stages, with a few experiments, to figure out what the decentralized web need. If you want to participate in one, write us to contact@esteroids.xyz or DM in Twitter.

## Decentralized websites availability is a problem
There are a few popular ways to access dWebsites: browser extensions, Brave and .eth.link gateway.

None of them works well. They all have downtime, they are all occasionally slow, and psychologically, very few people will visit esteroids.eth if it won’t be reliable and fast.

However, this seems like a problem with the tools but not with IPFS itself. How do we know? because if a dWebsite points point to an IPFS CID, which is available “since a while” in the network, and is well pinned, then it’s fast and reliable to access it using a native IPFS daemon.

There is, however, an inherent problem with dWebsites which update often, each time pointing to a different IPFS CID (using IPNS), since it takes time for this CID to become available to everyone fast

## It’s (still) hard to get ENS+IPNS right
In April-May we updated the ENS record of esteroids.eth on every change. But a website like Esteroids needs to be updated at least once an hour, so it ends up being super expensive.

By the end of May, we switched to point esteroids.eth to an IPNS value.

The difference between IPNS and IPFS is that IPFS links are fixed, but IPNS links can be updated all the time. This means that you just set up your ENS name once (pointing it to IPNS), and then do the IPNS updates for free.

Boy, did this worked terribly.

With IPNS, our website may always had the latest data, but it was was available maybe 70% of the time.

We worked hard to bring the website availability to a “reasonable“ condition, but it’s still not great. So ENS+IPNS is possible, but right now it’ssuper hard to get it right.

## Filecoin (still) doesn’t seem like a solution
It takes up to 24 hours to seal data in Filecoin, so at the moment it doesn’t seem the solution for decentralized websites that need to be updated often, and needs those updates to be available asap.

We’ll talk about it more soon.

## Brave is great (but..)
Brave supports .eth websites natively, and that’s great. What’s even greater, is that it works pretty well! Really, go to brave and type esteroids.eth → works, right?

So why just “pretty well” instead of “great”? Because Brave uses .eth.link service to resolve .eth. If .eth.link is down, Brave stops resolving .eth website.

This worry is not theoretical! Just last weekend Brave didn’t work for .eth websites for a few hours for this reason.

Btw, Brave does resolves .eth websites faster than .eth.link, even though it relies on .eth.link as a service! Magic? no:

Brave uses .eth.link only to resolve ENS values, but then uses its own internal mechanism to fetch the content from IPFS. Brave mechanism seems faster than .eth.link for the second step, so Brave works faster than .eth.link at this moment.

How should Brave go to improve its support for .eth websites? Well, we wrote a long article about it last month.

## dWebsites are the most exciting thing happening now on the internet
A few times a week we get this exciting feeling when someone creates an amazing innovative dWebsite. Here are a few examples:

- Penguin Swap is an interface for Uniswap.
- Penguin Party is a DAO for Penguin Swap.
- Ethereans OS is an operating system on top of Ethereum.
- The Ethereans OS people also do Covenants , ITEMS and Where is My Dragon?. They are one of the most exciting groups working in this sphere.
- Buidlerberg is a conference you find only in the dWeb!
- Smoke Signal is a place to publish articles.
- Dbuzz is a micro-blogging platform.
- Amethyst DAO is Experimental Metaverse Gaming Collective Built on Ethereum.
- Omen is a prediction market.

and so much more.

Check out esteroids.eth.link every day to see the new websites!

**[This article was originally published in Esteroids blog with small modifications]**