---
layout: post
title: Woolball - A Name System with Links
category: Woolball
date:   2022-10-25 00:00:33 +0100
comments: true
author: Neiman
description: Woolball is a name system with links; names can link to each other. This simple extension creates a whole new kind of a name system, with extra capabilities over the existing ones, like a native web3 accounts system, a reputation score for names, and structured DAOs.
tags:
    - Woolball, Name Systems
---

<img style="width: 200px; float: right; padding: 20px" src="{{ site.baseurl }}/resources/images/woolball/cat-with-woolball.png">

***TL;DR**. Woolball is a name system with links; names can link to each other.*

*This simple extension creates a whole new kind of a name system, with extra capabilities over the existing ones, like a native web3 accounts system, a reputation score for names, and structured DAOs.*

*Woolball is a flat name system! There is no hierarchy, as subdomains are replaced by links. It's also a cyclic system since names link to each other.*

*Links are written with a `#`, so a link from `alice` to `bob` is `alice#bob`.*

*Having all those links makes the graph of the name system look, well, like one big ball of wool.*

<img src="{{ site.baseurl }}/resources/images/woolball/woolballs.png">

## 1. Introduction
We introduce Woolball, a flat name system that uses links between names instead of subdomains.

These links create a new kind of name system with an internal social structure. It yields without any extra effort 
- a Web3 accounts system,
- a reputation score for names, and
- a tool for making a structure for a DAO.  

We believe links bring Internet name systems one step closer to how we handle identities in the physical world.

Woolball is a flat name system! It has no subdomains. We use links to replace them. Hierarchy is simply not needed.

Nevertheless, Woolball is an extension of subdomain name systems. Everything you could do with subdomains, you can also do with Woolball.

This article is a description of Woolball, not a technical specification. We tried to leave as many boring bits out but focused on what's different. We tried to make things clear, not accurate or tedious. 

Ready? Let's go! Or as we say in Woolball, "let's link!".


### 1.1. Wait wait! What's wrong with the subdomain system?
Well, nothing is wrong with it, we just don't think it answers the needs of a Web3 name system.

Look, people use Web3 name systems, like ENS, as their identity. That's clear, see crypto Twitter or any other Ethereum social interaction.

But how are subdomains connected to this identity? That's less clear.

When [Coinbase](https://help.coinbase.com/en/wallet/managing-account/coinbase-ens-support) give someone a subdomain, they kind of attest something about them. But since this attestation is completely separated from the person's main ENS name, it's almost invisible. 

Even worse! Imagine you get subdomains from more organizations ([OptiNames](https://twitter.com/optinames?s=21&t=ohRJcBEyBZvxGo37quLJ3w), [Decenterland](https://decentraland.org/blog/announcements/id-goes-di/), and [Bensyc](https://bensyc.eth.limo/) already hand out some). You'll end up managing dozens of subdomain accounts, so we're back to web 2.0 all over again.

Once you replace subdomains with links it all makes sense though. You don't need to manage dozens of accounts. You just manage yours. All the rest of your accounts are linked to it; they become part of your Web3 identity.

## 2. System Overview
Most name systems have only one main object, a name. Woolball, however, has two main objects, a name, and a link. Two! See? it's already *exciting*. 

There's only one layer of names in Woolball. Yup, no TLDs, no subdomains, and no hierarchy at all. There's simply no need for it. However, all the names in this layer are *unique*.

Ready? here comes the exciting part: each name can create links to other names (or to other links)!

Links are a one-directional arrow pointing from one name (linker) into another name or into a link (in both cases they are called linkee). 

Every link has an alias. That alias is unique among all the links coming from one name (so one name can't make two links with the same alias, got it?).

How do you call links? 

First, links are written with a `#`. A link from `alice` to `bob` is `alice#bob`.


But if `alice` made a link to `bob` and gave it the alias "BobThegreat", then `alice#BobThegreat` is the name of this link.

There's much more to say about links. How do you use them? What do they inherit from the names they link to? But hold your horses, we'll get to it in further sections.

Btw, you can imagine the graph of Woolball as being a collection of names with many links from one name to another. This looks like one big messy "ball of wool", hence the name.

## 3. Names
Woolball names are the basic object of the system. 

They're also the most boring object of the system since they're similar to other name systems. Let's not spend too many words on them.

The basic facts:
- The ID of the name is the hash of the name.
- Each name has an owner, a controller, and a resolver. The owner owns the name, the controllers operate it, and the resolver specifies its functionality. This is similar to ENS.
- Names are registered for a finite amount of time (but can be extended). 

    We didn't want to go down the path of giving away names forever, because we're afraid of eternity and afraid of losing names when people lose their keys.

Each name can create links (ta-dam!), or others can create links to it (ta-dam again!). This gives two interesting collections associated with each name:
1. A collection of all the links the name created.
2. A collection of all the links pointing to this name.

Who can extend names? The answer is not that simple, since there are now also links in the game. Let's discuss that in a new subsection.

### 3.1. Extension of names
We don't want to let anyone extend the registration of a name; it may cause dead names (where the owner lost the key) to become zombies and be registered to a ghost owner forever. 

But there's an issue also if we only let the owner of the name extend its own registration. 

Why? Well, when a name expires all the links it created disappear. However, some people may come to rely on those links; this makes it risky for them. 

To prevent the situation of names expiring before all of their links expire, we make the following rule for extending the registration of names.

> The registration of a name can be extended either by the owner of the name or by the owner of a valid link (as opposed to an "expired or canceled" link) that this name created.

## 4. Links
Let's get the boring bits out first. Like names, each link has
- a controller, 
- a resolver. 

However, *unlike* names, a link doesn't have an owner! Instead, it has three new fields. 
- from,
- to, 
- type. 

The fields 'from' and 'to' specify who created the link and to where it points. Both 'from' and 'to' can be either names or links.

the 'type' of the link determines who actually owns the link. By owning we mean the person who can cancel it, transfer it, etc. We describe the possible types in a section below.

Links have one more additional field, 'alias', which determines the name of the link. We'll discuss that as well in a separate section.

To sum it all up, a link object has the following structure.

```
Link {
    from: nameID
    to: nameID
    type;
    alias;
    resolver;
    controller;
}
```

The ID of a link is `Hash(ID of 'from' field, alias)`.

Last but not least, a link can also create other links from itself, and other names or links can link to it. 

So, similar to names, each link has two collections associated with it. 
1. A collection of all the links the link created.
2. A collection of all links pointing to this link.

Note that one name (or link) can make several links to another name (or link) as long as each got a different alias.

### 4.1. `ahmad#basia`
Links are written with a `#`. So if the name `ahmad` makes a link to `basia` it's written as `ahmad#basia`.

BUT -- if `ahmad#basia` has a contenthash of a website and is used as a URL in a browser, you need to write `greatBasia.ahmad`. See? you exchange the `#` with a `.`, and reverse the order of names in the link.

That's not our fault, that's how the URL standard is.

### 4.2. Alias
In the real world, identity has two components. One is what you claim about yourself, while the second is what others claim about you. 

For example, you may claim that you are "Ahmad the great", but you will not really be this person till enough people will think of you as "Ahmad the great". 

In some cases, your claim about yourself matters much less than what others claim about you.

A link and its 'alias' field is a way to equip an Internet name system with the concept of what others think of you.

Basically 'alias' is a string that is set by the person who created the link. If they choose not to set an 'alias', then by default the alias equals the name of the target of the link.

The field 'alias' is unique among all the links a name (or a link) creates. One name (or link) can't create two links with the same alias.

The field 'alias' determines how we call the link. We'll show it by example: 

If the name `ahmad` makes a link to the name `basia`, but doesn't set an alias, then the name of the link is `ahmad#basia`. However, if `ahmad` set the alias of the link to `greatBasia`, then the name of the link is `ahmad#greatBasia`. 

### 4.3. Types of links
The type of the link determines who actually owns it.

To keep it clear and simple, we defined only three types of links. These types give ownership of the link either to the linker, linkee, or a combination of both of them.

The types are as follows.

1. **Linker control**. The link is not transferable, only the linker can extend or cancel it.
2. **Linkee control**. The link is transferable, where only the linkee can extend, cancel or transfer it.
3. **Mixed control**. Both the linker and the linkee can transfer, extend or cancel the link. 

### 4.4. resolver and inheritance
An important feature of links is how they inherit data from the linkee.

By default, everything is inherited from the linkee. This means that if the resolver of the link is empty, then every query for data from the link is like a query to the linkee.

However, a link can override data from the linkee or extend it, by having its own resolver.

### 4.5. Woolball is an extension of subdomains name systems
We said that Woolball is an extension of the current name systems (DNS, ENS), so we have to justify that. Basically, we need to explain how you can do with links everything you can do with subdomains.

You can create two types of subdomains. Either a subdomain you give someone else (for them to have a cool name) or a subdomain you use for your own usage (like, for your email server).

A link to someone can do everything that a subdomain you gave to this someone can do. Easy.

But what's the equivalent of a subdomain you created for your own usage. Well, it's a link to yourself.

To be clear, links can do everything subdomains can do, but subdomains can't do everything a link can do. Hence it's an extension.

## 5. Interaction Between Links and Names
The power of Woolball comes out when considering the interaction between links and names. This interaction generates naturally three important systems:

1. Web3 accounts.
2. A reputation system.
3. Structured DAOs.

### 5.1. Web3 accounts
We explain how Woolball generates a Web3 accounts system by an example.

Let's say that a DAO called ExampleDAO wants to give an account to one of its members, Alice. How does it do that? It creates a link from `exampleDAO` to the name `alice`, leaving the alias empty.

... and that's it! Alice has an account in ExampleDAO called `exampledao#alice`.

In which sense is it an account? If ExampleDAO tries to get data from `exampledao#alice`, it sees the resolver is empty (since Alice didn't do anything yet). But then it *follows* the link to `alice`, and gets the data from the resolver of `alice`. 

See, there's no need for Alice to fill up anything new for this account.

This works also in the opposite direction. If Alice logs into ExampleDAO with the name `alice`, then the system follows the link *backwards*, recognizes that `alice` is also `exampledao#alice`, and approves the login attempt. 

That way Alice doesn't need to manage a new user name, but she can simply use her standard name for this account.

When does Alice define a new resolver for `exampledao#alice`? when she wants to override or expand the resolver of `alice`.

There are double benefits to this accounts system. 

On the one hand, it's super easy for anyone to make accounts for other people in their organization, Daaps, or platforms. On the other hand, people don't need to get lost in managing all these accounts; their main name is a global account for everything they use in web3.

### 5.2. Reputation
A link name system can generate a reputation score for names.

Just think how useful that is. You can screen spammers, bots, or all those things you don't like, based on their low reputation score. You can trust people you don't know because they have a high reputation. It will feel so much more comfortable communicating with strangers in a name system that has an internal reputation system in place, right?

There are several ways to create reputation systems for Woolball. We describe here one method. It's not necessarily the best one, but it's one of the simpler ones. 

Reputation is a subjective thing, so there is no such thing as a "perfect reputation system". The quality of a system is judged differently by different people

#### 5.2.1. A simple reputation system 
First, select a "trust set" of trusted names. This is a crucial step! The better the trust set is (like, the more reliable the names in it are), the more accurate the reputation score will be. 

Each name in the trust set has a perfect reputation score of a 100.

For each name outside the trust set, calculate how many names in the trust set created a link to this name. Each such link equals a point. If the name has a 100 points (i.e., at least a 100 different names in the trust set have a link to it), we add it to the trust set and recalculate the score of all the other names. 

We can easily extend this method to calculate also reputation points for links between names outside the trust set (but each such link would be worth less than one point). But we save such extensions for a different  article in order to keep the example simple.

### 5.3. Structured DAOs
Many DAOs have some internal structure, with stewards, delegates, secretaries, workgroups, subgroups, etc. See for example ENS DAO and Gitcoin DAO.

Right now those DAOs need an external tool to make and manage this structure, but with Woolball a structure can be made using the name system itself.

What if you got three stewards? Just give them all links from the name of the DAO in the style of `dao#stewards#steward1`. The same goes for workgroups or any role in the DAO.  It's also easy to update the rules when people change, you just updated the link!

Links are a simple way to give role X to the person with the name Y.

## 6. Integration with Other Name Systems
Integration with other name systems on the same blockchain is possible using a name wrapper contract. 

In this case, the name wrapper contract owns the name and provides the regular functionality (create a link, modify a link, etc), but the contract also performs some actions on the other name system.

For example, when someone asks a name wrapper contract to create a "link to itself", it also creates a corresponding subdomain in the other name system.

## 7. Summary
There is a lot of attention going into name systems in the last few months. Some of that is hype, but lots of that is because of need.

Web3 needs a good name system, and we think that the tech existing so far is great, but not perfect yet.

There's a path to walk before we get the mature name system Web3 deserves. We hope Woolball is a step in the right direction.

<img style=" float: right; padding: 20px" src="{{ site.baseurl }}/resources/images/woolball/uniwoolball.png">
## 8. Acknowledgment
There were many people who contributed to turning this article from a strange idea into a complete one. With no particular order, thanks to @zz9, @sshmatrix, @wolfram.eth, and @enspunks. I use the names I know you from Discord since I don't know the full name of everyone. Thanks goes also to Craig Sailor who doesn't have a Discord handle.

Chris Powers gave so many enlighting comments that he deserves a separate thank you. Fabio Saclini gave, as always, too many creative ideas for me to handle, but specifically had the brilliant proposal to represent links with a '#'.

Last but not least, thanks to @tomlightning and @elle from Esteroids who had to suffer me talking about this strange name system for almost 2 weeks. 

**(in the picture: Uniwoolball, generated by Fabio Scalini)**