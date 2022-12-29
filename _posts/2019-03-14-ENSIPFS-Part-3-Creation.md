---
layout: post
title: ENS+IPFS Part 3&#58; Building an ENS+IPFS Website
category: ENS+IPFS
comments: true
description: How to build an ENS+IPFS website? 
tags:
    - ENS+IPFS
---
### Last updated: 20-feb-2019
{: #LastUpdated }

{::options parse_block_html="true" /}
<div class="warning alert">
This is Part 3 of the ENS+IPFS posts. [Part 1]({% post_url 2019-03-12-ENSIPFS-Part-1-Introduction %}) described the technology while [Part 2]({% post_url 2019-03-13-ENSIPFS-Part-2-Accessing %}) explains how to access such websites. 
</div>

Sadly, we have to begin with a disclaimer.

{::options parse_block_html="true" /}
<div class="note alert">
#### Disclaimer 
If you ever worked with a nascent technology, you know how it goes: instructions from Monday morning are obsolete by Tuesday evening. 

It's hard to keep this post up-to-date (though we try!), so instead we do two things.
1. Notify on the top of the post ([here!](#LastUpdated)) when was it last updated.
2. Focus on the general process and steps to make an ENS+IPFS website, since the general process changes less often than the exact technical details. 

Knowing the process, the reader can complete the technical details on his own, even if those here are outdated. 
</div>

Setting up ENS+IPFS websites take four steps.
1. Registering an ENS name;
2. Creating a static website;
3. Uploading the static website to IPFS (this returns the IPFS address of the website). 
4. Updating the ENS record with the IPFS address of the websites. 

You need to repeat steps 2-4 each time you update the website.

## Tools
1. **IPFS**. Standard [IPFS](https://docs.ipfs.io/introduction/install/) software.
2. **Ethereum node**. [Parity](https://www.parity.io/) or [Geth](https://github.com/ethereum/go-ethereum/wiki/geth).

Here things become less standard...

{:start="3"}
3. **ENS Dapp** (websites to use ENS). There is no one website that gives all options at the moment, see options in each step.
4. **Dapp Browser**. Ethereum nodes run locally, and normally browsers don't allow Dapps to talk to local addresses directly (for justified security reasons). A Dapp browser is a component that connects Dapps to Ethereum nodes. Parity got their own browser, and geth is often combined with Mist. However, we used [Metamask](http://metamask.io/) addon for Firefox.

## 1. Registering an ENS name
Registering an ENS name takes five days. It consists of the following steps.
1. Open an auction and bid on the name (72 hours = 3 days);
2. Reveal the bid (48 hours = 2 days);
3. Finalize the purchase (after the reveal the bid option is over).

Where do you do those steps? Good question. At the time of writing the [ENS website](http://manager.ens.domains/) doesn't offer this service, but instead refers to other websites. 

The main option is [My Ether Wallet](https://www.myetherwallet.com/#ens). But we tried My Ether Wallet out, step 1 (opening an auction) worked well, while steps 2 and 3 did not. To do those steps we used [My Crypto](https://mycrypto.com/ens). However, the app there is only in the "legacy" website, which is not a good sign.

## 2. Creating a static website
We used Jekyll, though there are many alternatives.

{::options parse_block_html="true" /}
<div class="success alert">
**Tip**. To generate a static website from a Jekyll daemon, run: 
```
wget --convert-links --adjust-extension -r http://127.0.0.1:4000/
```
where you replace `http://127.0.0.1:4000/` with the address of your local Jekyll service.
</div>

## 3. Uploading the static website to IPFS
We recap the steps here quickly though you can find them in any IPFS tutorial. 

Add the website to IPFS.

```
ipfs add -r <directory of website>
```
The last hash is the output of this command identifies your website. Let's call it `WebsiteHash`.

Start the IPFS daemon to make the website accessible.
```
ipfs daemon
```
To verify that the website is really accessible to IPFS users, test it in `https://ipfs.io/ipfs/WebsiteHash/`, where `WebsiteHash` is the the value you saved before. You may need to refresh a few times before the websites spreads to the whole IPFS network.

## 4. Updating the ENS record to point to the IPFS address of the website
Managing your ENS domain name in the following URL.
```
https://manager.ens.domains/name/YOURDOMAIN.eth
```
(where YOURDOMAIN is the name of your ENS domain).

What's left to do is to link the ENS to the IPFS address. However, that's not as simple as you may think..

ENS doesn't simply give you a "free variable" to write whichever info you want on. Instead you need to tell ENS an address of a smart contract. This smart contract handles writing and reading of data associated to the ENS name.

ENS team supplies a "public resolver" for the common users. They just [updated the public resolver](https://medium.com/the-ethereum-name-service/the-new-ens-manager-now-supports-eip1577-contenthash-82e2d6724fae) on the 31st of January to support multihash values (including IPFS addresses). 

To set a resolver press the blue button 'SET' near the Resolver name. Then you can either give your own resolver address, or choose the option "Use Public Resolver".

If you use the public resolver, you can next link an IPFS address to your ENS domain. Simply press the '+' button in the records area, and add an IPFS record beginning with "ipfs://WebsiteHash" (where WebsiteHash is the hash you saved in Step 3 while putting your website in IPFS).

The **problem** is that the tools to view ENS+IPFS websites still didn't catch up with the new public resolver. We use a wordaround till they catch up.

### 4.1 Temporary workaround till tools adjust to the new public resolver
To get your website accessible by tools like Metamask and Status, do the following.
1. Set the resolver to the old public resolver address: `0x1da022710dF5002339274AaDEe8D58218e9D6AB5`. You'll get a warning, get used to ignore warnings;
2. The old resolver doesn't support IPFS addresses directly! Instead, you need to transform the IPFS address to a hex value. You [this tool](https://codepen.io/phyrex/pen/MBzOGR) to do that.
3. Add the hex value from the previous step as the content for the ENS record

Your ENS+IPFS website should work now!

**[This article was originally published in Almonit blog with small modifications]**
