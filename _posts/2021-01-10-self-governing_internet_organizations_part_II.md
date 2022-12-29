---
layout: post
title: The Self-Governing Internet Organizations Manifest (Part II)
category: SGO
date:   2021-01-10 00:00:33 +0100
comments: true
author: Neiman
description: Introducing the idea of self-governing Internet organizations
tags:
    - SGO
---
Self-governing Internet organizations (SGOs) are online organizations which are owned and controlled by their own users.

In [Part I of this article]({% post_url 2021-01-08-self-governing_internet_organizations_part_I %}) we laid the philosophical principles that undermine SGOs, while this part is about their technical implementation. Specifically, we suggest implementing SGOs using DAOs, and discuss the pros, cons, possibilities and limitations of DAOs.

## DAOs, or how to build self-governing Internet organizations?
While it is easy to call for the establishment of SGOs, how to build them is another question. The current legal framework is not exactly designed for global, international dynamic organizations like this.

The solution we propose here is a tool for Internet organizations called "DAO".

DAOs were invented during the 2010s and were used in more than a few Internet organizations in the last few years, such as Metacartel, MolochDAO, MakerDAO, dxDAO, and many others.

We suggest to take this tool, already existing, and use it for creating SGOs. 

The rest of this article focuses on what is a DAO, and which kind of organizations can be built using it?

### Part I: DAO introductions
A DAO, Decentralized Autonomous Organization, is a programmable organization. 

DAOs are described by computer code (instead of by legal language) and are registered on a blockchain (instead of with a state). The latter step is what puts the "decentralized" and "autonomous" word in its name.

While you need a lawyer to implement a classical organization, you need a programmer to implement a DAO. This approach has both pros and cons. 

The pros are that everyone is equal in front of the code, while the code also allows dynamic fast changes in the organization. DAOs easily enables International organizations because code doesn't care who you are or where you are, and allows for organizations to develop quickly.

Cons? A programming language might be a bit *too strict* for human agreements. While legal contracts describe organizations accurately, they always leave space for human interpretations. This is more difficult to achieve with code.

Are you familiar with the common legal phrase "reasonable time"? How would you write such phrases in code? How would the blockchain, operating the DAO, would be able to assess "reasonable time"? Enabling such phrases is important, otherwise, we're at the risk of entering a state of "code is law" or "automated justice", not exactly what we want for human organizations.

DAOs solve this issue by accurately specifying, in the code, which parts can be assessed automatically by the blockchain, and which parts need to be assessed, including how the assessment happens, by outside entities.

In the case of "reasonable time", the code might specify, for example, that what is "reasonable time" is assessed by three members of the DAO, and that they assess it by majority voting (if 2 of them vote that a reasonable time has passed, then indeed, a reasonable time has passed). 

You can easily elaborate on this method for more advanced structures. For example, letting the whole organization decide on such a matter (democracy), asking outside organizations to decide (arbitration), or even let outside institutes make assessments of those topics (Internet court system).

There are plenty of other DAO-related topics to discuss. What are the best practices in designing a DAO? What is the members' liability for the DAO actions? 

But we rather focus on practicality, so instead of discussing those questions, let's take a look at what DAOs can already do very well, and what DAOs might do very well in the near future. These things dictate which kind of SGOs can be implemented using a DAO.

### Part II: DAOs, state of the art
To see what an organization based on a DAO can do, let's examine which kind of techniques are used nowadays in DAOs. These techniques belong to one of five categories.

1. **Controlling crypto assets**. DAOs are ideal for managing things like crypto tokens, decentralized names, or other NFTs (non-fungible tokens). 

   The basic example is when DAO members collect a large number of cryptocurrencies together and manage these funds via voting.

2. **Registries**. Registries are a collection of records, containing information that was agreed upon by some community. For example, the state property registry contains information of which property belongs to who, as agreed by the citizens of the states.

    DAOs are a very good tool for creating and maintaining registries, showing which data DAO members agree on. 

3. **Staking**. Staking is a method to ensure DAOs against the misbehaviour of members. Staking is used mostly with members holding a position of trust.

   In staking, a member transfers some funds (called, "stake") to the DAO. The DAO holds the funds as long as the member holds the position on trust. If the member betrays the trust, the DAO members can decide to confiscate some, or all, of the stake. The stake is returned to the member once the position of trust is relinquished.

4. **External blockchain services**. DAOs can use services of other DAOs running on the same blockchain.

4. **External non-blockchain services**. DAOs can use services provided by third parties outside the blockchain, under the principle that those services should be interoperable and replaceable to minimize dependencies on the third party.

    An example of this when a DAO pays a third party to maintain full nodes of the blockchain it is registered on. 

### Part III: The possible future of DAOs
While the previous section was practical (it contained actions DAOs already take nowadays), this action is pure speculation, hence "wilder". 

It is almost a science fiction section, not a prediction. Take what's written here as possibilities for what DAOs may do in the future, treat them with a grain of salt.

We present each possibility in form of a change that needs to happen, and what it would enable for DAOs.

**Changes giving new options for DAO.**

1. **Services for DAOs.** In the same way that services, any kind of services, are being offered to companies, they could also be offered to DAOs. Some such services would be: social media accounts for DAOs, through cloud computing, and food deliveries.

   Such services should offer login for DAOs, and be able to communicate with the DAO to know which members have access to the service at any given time.

**Changes letting DAOs be used for any kind of organization, from Google to Amazon.**

2. **Creation a legal framework for DAOs**. For some people, a legal framework recognizing a DAO as a legal entity is the ultimate goal. With it, DAOs could do anything a traditional organization can do.

   Is it possible to create such a legal framework without destroying the fundamental aspects that make DAOs so special? Could we still have inclusive DAOs, where members can be from anywhere in the world, while their location and national identity have no effect - or even unknown - to the other members of the organization?

   If a DAO is recognized by a legal system of a specific state, it may violate the "Members equality" principle of self-governing Internet organizations ([see here]({% post_url 2021-01-08-self-governing_internet_organizations_part_I %})), since it would create an advantage for people located in that specific state. Recognizing DAOs as International organizations may assist in that, but this privilege is reserved, at the moment, only for unique entities, such as the UN. 

3. **Imitating the legal framework ("World of DAOs")**. Our legal framework can be thought of as a hierarchical structure of legal entities. 

   At the top of the hierarchy, there are UN organizations and states (each state is a legal entity, while together they form the UN legal entity). On lower levels, there are legal entities (organizations) and human entities recognized by some state. Each organization is further composed of other legal entities (either human entities or other organizations).

   This hierarchical structure can be directly copied by DAOs. A few big DAOs will be equivalent to states, together they will form the "UD" (united DAOs). Each DAO would be able to give a DAO "legal status" to other smaller DAOs, or to "Internet entities" (the Internet equivalent to human entities).
    
    This structure gives DAOs much more power in governing its members and members of other DAOs, introducing many new capabilities.

**The following change would create a clear, moral Darknet**

4. **Darknet becomes a DAO**. The darknet gained a bad reputation, possibly justified, due to its absolute lack of governance. If Tor transforms itself into a self-governing Internet organization in the form of the DAO, where the members are darknet users (that can remain anonymous), then this DAO could moderate the Darknet, blocking bad actors from it, while keeping Tor famous privacy features.

**The following change will create a terrible dark spin on DAOs**

5. **Used by crime organizations**. This is sadly a very probable option. Crime organizations already function outside the legal system, so they could benefit from switching to a DAO model. 

**The following change will create space DAOs!**

6. **Human settlement of other planets**. Once humans start settling on other planets, enforcing powers of the inter-planetary legal system becomes quite limited. But DAOs come to the rescue, offering a space legal system enhanced with cryptography! 

   Yes, we are joking, we told you it's a science fiction section.

## Call for action
If you got hooked on the idea of self-governing Internet organizations and DAOs, you should either join Almonit's Alpress project in the effort to create one or consider it for your projects.

To join Almonit follow us [on Twitter](https://twitter.com/GoAlmonit), join [our Telegram group](https://t.co/Z79kgx8noD?amp=1), or drop us an email (contact@almonit.club) to get involved in the project.

To consider it for your project, check out existing DAOs frameworks such as DAOStack or Aragon, or consider programming your DAO if you want your design.

## Summary
Digital life is real life, and it's hard to imagine a future where big tech keeps on controlling it. The idea of people governing their social structures is too strong in society at this point in history.

Everything is ready for self-governing Internet organizations to make their stand.

## Acknowledgement
Thanks to Krzysztof Lewosz, Muhammed Tanrıkulu, Eylon Aviv, and Craig Sailor for participating in the preparation of this article. 

**[This article was originally published in Almonit blog with small modifications]**