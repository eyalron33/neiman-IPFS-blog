---
layout: post
title: ENS+IPFS Part 1&#58; Introduction
category: ENS+IPFS
comments: true
description: What is ENS? What is IPFS? How these technologies are used to store this website? a guide for the Perplexed 
tags:
    - ENS+IPFS
---
{::options parse_block_html="true" /}
<div class="warning alert">
This is Part 1 of the ENS+IPFS posts. [Part 2]({% post_url 2019-03-13-ENSIPFS-Part-2-Accessing %}) explains how to access such websites, while [Part 3]({% post_url 2019-03-14-ENSIPFS-Part-3-Creation %}) explains how to create them.
</div>

There are two ways to access this website.

One is "boring", with `almonit.club`. The other is adventurous, with the non-standard address `almonit.eth`.

What's the difference between the two?

Almonit.club is hosted like a normal website. It is stored on a server, and the name almonit.club is registered with a regular name service (DNS). To access almonit.club, the browser first asks the DNS in which server it is stored, and then gets the website from that server.

With almonit.eth website we took a bit different approach. Instead of a server, we use IPFS, and instead of DNS, we use ENS. 

#### IPFS  <img style="width: 120px; float:right;" src="{{ site.baseurl }}/resources/images/ENSIPFS/IPFS.png">

IPFS is a peer-to-peer protocol to store data. There are some similarities between IPFS and BitTorrent. 

For example, similar that in BitTorrent data needs at least one seed node to be available, in IPFS websites need to be on at least one node. As long as we make sure that one such node exists, our website will enjoy all the regular advantages of P2P network (resilient, censorship-resistance, sharing resources of others and more).


Every IPFS data has an address (called a hash). To access almonit.eth, you need to know the address of its latest version. The address changes every time the websites updates. 

#### ENS <img style="width: 120px; float:right;" src="{{ site.baseurl }}/resources/images/ENSIPFS/ENS.png">
ENS is the Ethereum Name Service. It serves the same rule that DNS does in the traditional website settings. While DNS tells the server where a website is stored, ENS tells what is the latest IPFS address of the website. 

ENS has a few advantage. It's censorship resistance; as far as the Ethereum blockchain is available, ENS also is. It's also pseudonymous, cheaper (in most cases) than DNS, and got a nice anti-squatting mechanism (squatting is when people buy popular names they don't need, in order to sell it for others for expensive prices).

#### ENS+IPFS <img style="width: 274px; float:right;" src="{{ site.baseurl }}/resources/images/ENSIPFS/ENSIPFS.png">

To access almonit.eth, you first ask ENS what's the latest IPFS address of the website, and then ask IPFS for the website itself. 

Sounds complicated? don't worry. There are tools for accessing ENS+IPFS websites, and they are explained in the next article, [ENS+IPFS: part 2]({% post_url 2019-03-13-ENSIPFS-Part-2-Accessing %}).

ENS+IPFS websites are as censorship resistance (but easier and cheaper to make) as Darknet websites, but much less anonymous. We don't really need it for Almonit; but hey, ain't we allowed to do things just for the heck of it? 

<div class="success alert">
Both IPFS and ENS are still in experimental stage. The tools for using them are immature, and in the case of ENS even the technology itself still changes quite often. Don't use ENS+IPSF for the polished experience in this point of time, use it for research purposes. 
</div>

**[This article was originally published in Almonit blog with small modifications]**