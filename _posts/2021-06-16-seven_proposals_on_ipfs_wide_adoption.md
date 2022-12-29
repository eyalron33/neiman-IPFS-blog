---
layout: post
title: Seven proposals on how can IPFS reach wide adoption
category: SGO
date:   2021-06-16 00:00:33 +0100
comments: true
author: Neiman
description:  What does IPFS need to do in order to reach wide adoption?
tags:
    - dWebsites, IPFS
---
**Q**: What does IPFS need to do in order to reach wide adoption?
**A**: We have no purple clue!

So [we asked the smart people of Reddit](https://www.reddit.com/r/ipfs/comments/ntm85c/what_do_you_think_we_need_to_increase_ipfs/h0wgz3t/?context=3), and got some gooooood feedback in return.

The proposals raised there can generally be divided into two groups:
- proposals regarding decentralized websites (like ENS+IPFS),
- proposals regarding IPFS own features.

## Proposals regarding dWebsites (Decentralized Websites)
As you know, [Esteroids](https://esteroids.eth.limo/#/) is a hub for dWebsites. We especially like the following proposals.

### 1. More dynamic dWebsites

At first sight, people think dWebsites are like sending a zip file to a friend. But there are actually lots of dynamics possible in dWebsites!

How? You can use ENS or IPNS to update the dWebsite content, or use IPFS data structure to dynamically fetch content based on user’s actions — or even, you can use the blockchain like a server-side for dynamic content.

So why did people mentioned they want more dynamic dWebsites? Two reasons.

First, certain things are trivial for classical websites but are almost impossible, at the moment, for dWebsites. Simple things, like user comments or forums.

But the second reason, which is what we stress now, is that the limits of dynamic dWebsites are not yet researched.

Yes, we got some good projects like orbitDB or 3box, but they both need more time to mature, while the community needs much more than two such projects to experiment with dynamic dWebsites.

### 2. Add unique added value (our proposal)
So we talked about dWebsites imitating web 2.0, but how the hell would IPFS attract users by merely imitating what’s already exists?!

What we need are dWebsites that are dynamic in a way that web 2.0 websites can only dream of. We mean stuff like [SGOs]({% post_url 2021-01-08-self-governing_internet_organizations_part_I %}), where users actually own the platform.

Web 3.0 can offer unique dynamic behavior that stems out of its properties, but it needs people to experiment and buidl frameworks for that.

It’ll happen soon, we’re also working on such things.

### 3. Logins
As one commenter astutely put it, “IPFS struggles to host a plaintext bulletin board with logins like you’d find in the late 80s”.

So yup, logins are important. Logins are the way for people to create a consistent online identity, to have continous dialogues, to get others to know them.

But logins are also a way to authenticate who you are, and to prove that you are the same person who did an action a week ago. This concept is not alien neither to crypto nor to the decentralized world. There are DIDs, self-sovereign identity, or ENS login.

There are forms of login possible in dWebsites, waiting for someone to implement them.

## Proposals About IPFS Own Features
### 4. IPFS library for mobile

Well, there is [gomobile-ipfs](https://ipfs-shipyard.github.io/gomobile-ipfs/) (we didn’t try it yet though), but people claim it’s not enough.

### 5. Statistics and analytics
How many people saw your website? How many pin it? How can you know what users like? How can you communicate with visitors?

Or in other words: how can you get dWebsites analytics without violating users’ privacy? That’s a million-dollar question, we’re sure someone is working on it.

### 6. Speed up IPNS
We switched esteroids.eth.link to IPNS a few weeks ago, and we are kind of happy about it. Why “kind of”? well. as someone in Reddit said, IPNS is slow; it makes a bad first impression on visitors.

Speeding up IPNS should be a priority of IPFS. We may find out in the end that IPNS is would become more popular than IPFS itself.

### 7. Improve IPFS pubsub (our addition)

It’s also connected to the first proposal, “dynamic dWebsites”.

Pubsub is an experimental IPFS feature letting people create kind-of “chatrooms”.

The current version requires people to be connected to each other (either directly or indirectly), and if you don’t establish some connection between nodes, messages often get lost.

For dWebsites to have advanced functionality, IPFS should make it a top priority to speed up pubsub development.

Pubsub opens up a whole new world of possibilities for dynamic dWebsites, including chatrooms, encrypted chats and a million other options.

Really, just bring it to maturity, we’ll take care of the innovation.

## Summary
We collected seven proposals on how to accelerate IPFS adoption, but there must be dozens more we didn’t mention.

**[This article was originally published in Esteroids blog with small modifications]**