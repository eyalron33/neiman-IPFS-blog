---
layout: post
title: How should browsers integrate decentralized websites?
category: SGO
date:   2021-05-26 00:00:33 +0100
comments: true
author: Neiman
description: The dWeb is the future, but how should browsers integrate it without breaking its decentralization?
tags:
    - dWebsites, ENS, IPFS, Brave
---
If you tried recently (May 2021) to access the dWebsite (decentralized website) uniswapexchange.eth using the popular .eth.link gateway (uniswapexchange.eth.link), you got the following message.

<img style="width: 640px; border:1px solid #021a40;" src="{{ site.baseurl }}/resources/images/browsers-integrating-dwebsites/ethlink_error.png">

However, if you used a dWebsites browser extension ([Esteroids](https://addons.mozilla.org/en-US/firefox/addon/esteroids/), for example), you got the more familiar Uniswap interface.

<img style="width: 640px; border:1px solid #021a40;" src="{{ site.baseurl }}/resources/images/browsers-integrating-dwebsites/unswap.png">

The gateway .eth.link is [operated by Cloudflare](https://medium.com/the-ethereum-name-service/ens-partners-with-cloudflare-on-improved-eth-link-service-4801bf9148ff) since January 2021. For a majority of dWebsites users, those links are the only way they access dWebsites right now.

Cloudflare blocked uniswapexchange.eth in order to avoid confusion since it’s not Uniswap official link (uniswap.eth is). While their decision is reasonable, it does show how fast can the dWebsites ecosphere runs into centralization.

There are those who say that this situation will be solved once the main browsers integrate native support for dWebsites, but would it really? If browsers would implement it, let’s say, by taking all the data from Cloudflare, would it solve anything?

There were 23 dWebsites when Almonit launched its directory in September 2019. A year and a half later the number is almost 1000. At this rate next year it will likely exceed 10K, and the year after that a 100K. At some point we’ll reach the 1 million dWebsites mark, and who knows where it will stop?

Inevitably, the major browsers will add native support for dWebsites. There are already buds of it in Opera and Brave browsers (and other). But it won’t be easy for them to integrate dWebsites without breaking what makes them unique.

We are here to help them.

**Disclaimer**. While this article focuses on ENS+IPFS dWebsites, a lot of what’s written here is true, with minor modifications, for other kinds of dWebsites, like those based on Unstoppable domains, Swarm, Handshake, or Skynet.

## Desired properties
We want to use dWebsites in a way that is private, decentralized, and reliable.

Privacy is when as few entities as possible know you visited a dWebsite. If the number is zero it’s called “anonymity”, but we won’t insist on it.

Decentralization is when different people get data from different sources. If most people get the data from one entity, it gives this entity too much power, enabling it to eventually set its own standards for the field (cf., Google with Gmail or Chrome).

Reliability is when you know that you get the correct data, instead of, for example, instructions for planting cucumbers when you try to access uniswap.eth (though it would make a good April’s fool day joke).

## How DNS works?

To avoid reinventing the wheel, let’s see how things similar to dWebsites are used in browsers, for example, DNS.

Browsers don’t implement DNS by themselves, nope. They let the operation system (OS) do that. What browsers do is using the DNS API provided to them by the OS.

The OS in turn queries a DNS service (one or more, though normally one). By default, it queries the DNS service of your Internet provider, but since these have been either unreliable or violating people’s privacy in the past, many switched to Google DNS service (8.8.8.8) which is reliable, or Cloudfair (1.1.1.1) which is privacy-preserving.

Can you run your own DNS service? Yes, you can! But it’s uncommon with [plenty of reasons why not to do that](https://serverfault.com/questions/118020/running-a-recursive-dns-server-on-localhost).

Is it reasonable to request from the OS to provide similar ENS and IPFS APIs? Yes and no.

The OS supplies DNS API because the browser is not the only application using DNS. Almost every app uses DNS nowadays, so it makes sense for the OS to supply it. This “truth” goes also for Ethereum and IPFS. It’s not only browsers that supposed to use them, but potentially many other apps in the future.

On the other hand, the OS can supply DNS API because there is only one main DNS system. However, there are many blockchains and many decentralized file systems (sorry Bitcoin and Ethereum maximalist!), and we can’t expect OS devs to support all of them. They are busy people; they have an OS to write after all.

To complicate things further, many browsers started supporting, some even by default, DNS-over-HTTPS (or even better, Oblivious DNS-over-HTTPS). In this method, browsers use the operating system DNS much less and mostly resolve DNS requests on their own.

## How to support ENS + IPFS dWebsites?

Whether the OS supports ENS and IPFS, or the browsers themselves implement it, at some point someone will need to do that. Let’s discuss how.

In general, browsers require two steps to resolve ENS+IPFS dWebsites. First they retrieve the value of an ENS name from the Ethereum blockchain (like, esteroids.eth). Then they fetch the relevant contents from IPFS.

We will discuss these two steps in reverse order to reflect the level of difficulty required, beginning with IPFS.

## Getting data from IPFS
Two browsers (Brave and Opera), and a handful of browser extensions (Almonit, Unstoppable Domains, Metamask) already support IPFS websites. We have plenty of practice to base our proposal on.

### What do tools do so far?
Let’s face it, the best way of using IPFS is to run a go-ipfs daemon on your machine. The browser then simply queries the IPFS daemon for information. That’s what the IPFS companion addon does, and Brave already includes it natively.

While this way is a decentralized and reliable way, it is not very private (because IPFS is a peer-to-peer network that is not very private). What’s worse, you can’t run go-ipfs on your phone (it’ll drain the battery) or on weak networks (it’ll jam them). I personally brought down the Internet of many good cafes and hotels over the last few years by running the go-ipfs daemon.

For people who don’t want to run go-ipfs themselves, there are easier browser solutions. Brave, for example, lets you install go-ipfs node in the browser (they reported [over 50K installations in 60 days](https://twitter.com/brianbondy/status/1372937229002215428)), while Unstoppable Domains browser extension does a similar thing with js-ipfs. It has exactly the same pros and cons as installing go-ipfs yourself.

But probably the most popular option for using IPFS is gateways. This means that each of your IPFS requests is redirected to some IPFS gateway. Brave does that, and so do Esteroids, Unstoppable Domain, and Metamask browser extensions.

This way preserves privacy (only the gateway maintainer knows where you surfed). However, it contains many (many!) risks. What if all the tools redirect to one gateway? We would lose decentralization. This already happens now where many tools just redirect to dweb.link gateway. Additionally, there’s the issue that the data you get from the gateway is not being authenticated.

### How tools should use IPFS?

We make four calls to action for the IPFS ecosphere

1. **Create a “smart” IPFS daemon**. This daemon will adjust how it works based on the device and network it runs on. On a strong network and computer, it will act as it does right now, but on a weak network it may choose a low number of peers, and on weak devices, it will redirect to gateways.

2. **Gateway selection: decentralization by randomization**. A different gateway will be chosen for each session in order to prevent centralization. The level of decentralization can be calculated using the [Balls into bins](https://en.wikipedia.org/wiki/Balls_into_bins_problem) problem calculations. This method is already implemented in Esteroids Browser Extension.

3. **A business model for gateways**. There is no common business model for establishing and maintaining gateways yet. As it is obvious the dWeb can’t rely on philanthropic gateway maintainers for the long run, the community should work together to come up with ideas for the gateways business model. Skynet is working in this direction over the last few months.

4. DAOs, such as DXdao, should run their own IPFS gateway. This can be either for the public benefit or for their members based on a subscription model.

## Getting data from Ethereum

To use ENS you need to get data from the Ethereum blockchain. Well, there’s bad and good news about that.

The bad news: If you thought using IPFS is hard, using Ethereum is sevenfold harder.

But there is (kind of) good news! It’s not only a problem of the small dWebsites ecosphere, but of all the huge, rich, resourceful Ethereum ecosphere. With a bigger userbase comes greater resources dedicated to solving problems.

### What do tools do so far?
The best way to use Ethereum is, once again, to run an Ethereum client locally and have the browser querying it. That’s a decentralized, reliable, and even private solution. Perfect!

However, it’s also veeeery hard to do, since Ethereum clients eat your resources like it was a bar of tasty Belgian chocolate.

You can, alternatively, run a client on some external device or server. But that’s expensive! It requires knowledge, requires configuring the browser to use it. Not exactly a solution for muggles like myself.

Can browsers run Ethereum clients themselves (like what Brave does with go-ipfs clients)? No, that’s too complex.

So what everyone ends up doing, and I mean everyone, is using “some” gateway. By “some” gateway I mean obviously “an Infura gateway” (though we don’t really know what Brave uses to be honest). Is this good for decentralization, censorship resistance, privacy, and reliability? You know the answer yourself already.

**side note**. L2, side-chains, and Ethereum 2.0 do not seem to improve this situation much.

### How tools should use Ethereum/ENS?
Let’s face it, most Ethereum users are not going to run their own Ethereum clients in the near future. In light of this, we make 4 proposals, similar in spirit to our proposals for IPFS.

1. Create Web3 provider business model to increase the number of gateways. The community should come up with a business model for Web3 providers. This can be either be in the protocol level (paying web3 providers like you pay miners) or by a more traditional business model.

2. The Ethereum community and DAOs should create their own web3 service. If not public ones, then at least as a service for their own members.

3. Decentralization via randomization method for Web3 providers. see IPFS proposals, item 2.
    Accelerate development of light clients. How do users verify the data received from web3 providers? Right now they don’t. [Light clients](https://eth.wiki/en/concepts/light-client-protocol) suppose to enable it.

## Proposal: certificate of decentralization

The road for browser integration of dWebsites is a long and difficult one. It requires the involvement of many different players doing many different steps. Until that happens, we are going to see many hybrid solutions, or many great ideas this article did not think of.

**The certificate of decentralization** should be awarded on an ongoing basis by a coalition of DAOs in the blockchain space. This would give users an indication of how good is a current implementation of a product.

Such a certificate should be awarded for general blockchain products, not only to ones related to dWebsites.

**[This article was originally published in Esteroids blog with small modifications]**