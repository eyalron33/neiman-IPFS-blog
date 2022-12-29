---
layout: post
title: ENS+IPFS Part 2&#58; Accessing ENS+IPFS Websites
category: ENS+IPFS
comments: true
description: A guide for accessing websites ENS+IPFS websites
tags:
    - ENS+IPFS
---
This website is accessible in an ENS+IPFS version, [almonit.eth](http://almonit.eth/). 

[Part 1]({% post_url 2019-03-12-ENSIPFS-Part-1-Introduction %}) explained what ENS+IPFS websites are, and this part explains how to access such websites. [Part 3]({% post_url 2019-03-14-ENSIPFS-Part-3-Creation %}) explains how to create them.

### Option 1: Status browser (highest quality, mobile phones only)  <img style="width: 120px; float:right;" src="{{ site.baseurl }}/resources/images/ENSIPFS/status.png">
[Status browser](https://status.im/), also called a "mobile Ethereum OS", supports ENS+IPFS websites *only* for Android (Desktop version doesn't support it and iPhone version is in beta status). That's the easiest option to access almonit.eth.

Limitations? Status is available only with the Google Play Store (hey! not everyone use Google Store!), and apparently it doesn't support *all* android devices (such as, hmm, mine). That said, the company aim for blockchain values such as privacy and decentralization (their [FAQ](https://status.im/docs/FAQs.html) is honest and great).
 
Cons? Requires to open a Status and Ethereum account.

{::options parse_block_html="true" /}
<div class="success alert">
Both Status and Metamask (described below) require to open a software account (=password) and to have an Ethereum account. That's because both softwares are general Ethereum tools and not dedicated ENS+IPFS solutions.

In theory no accounts are needed to access ENS+IPFS websites; The future should bring simpler tools.
</div>

**Installation**: [Google Play Store](https://play.google.com/store/apps/details?id=im.status.ethereum).

### Option 2: Firefox + Metamask (moderate quality, all devices)<img style="width: 120px; float:right;" src="{{ site.baseurl }}/resources/images/ENSIPFS/metamask.png">

[Metaamask](https://metamask.io/) is a general and relatively easy ENS+IPSF solution (powered by [Portal Network](https://www.portal.network/)) for both mobile and desktop devices.

It works, but with hiccups. 

Cons? As with Status, Metamask and Ethereum accounts are needed. 

**Installation**: Install [Metamask plugin for Firefox](https://addons.mozilla.org/en-US/firefox/addon/ether-metamask/) and open an account.

{::options parse_block_html="true" /}
<div class="success alert">
**Metamask with a local Parity node** 

For extra security and privacy use a local Parity node with Metamask (instead of Metamask Ethereum node).

For this start parity in a light node (for fast synchronization, though be careful! it's an experimental option!), and allow JSON RPC calls (meaning, allow other apps to talk with your Parity node). You do it (after [installing Parity](https://wiki.parity.io/Setup)) with this command.
```
parity --light --jsonrpc-cors all
```
Note that this allows *all* software to talk to your Parity node, and is quite unsafe. Investigate further if you want to lunch parity while giving access to Metamask only.

Same is possible with a local geth node.
</div>

### Manually (all devices, decentralized, inconvenient)
<div class="note alert">
For power users only at the moment.
</div>

In theory you can also access ENS+IPFS websites manually.

What you need is the content of the ENS domain. Using this content with IPFS, either via a local IPFS node or a public IPFS gateway such as
`https://ipfs.io/ipfs/`.

In practice, this method can only be used (without extra steps) if ENS content format is the same as IPSF format. The ENS manager only [started supporting contenthash in February 2019](https://medium.com/the-ethereum-name-service/the-new-ens-manager-now-supports-eip1577-contenthash-82e2d6724fae) (including IPFS), and it will take some time for website and apps to catch up with it.

### Future options: Opera and Brave browsers
It was announced that both Opera ([here](https://twitter.com/ensdomains/status/1102884419017297921)) and Brave ([here](https://twitter.com/ensdomains/status/1105565560224563202?s=19)) browsers will adopt ENS+IPSF in the future.

**[This article was originally published in Almonit blog with small modifications]**