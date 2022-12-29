---
layout: post
title: The Short History of dWebsites
category: dwebsites
comments: true
description: When and how dWebsites began? Join us to a trip through the history beginning in the prehistoric days of the 2010s.
tags:
    - dwebsites
---
{::options parse_block_html="true" /}
<div class="warning alert">
Almonit is developing an ENS+IPFS plugin for Firefox. 

Would you like to be the first to try it out? Please do! Contact us at: contact@almonit.club . All we ask in return is an honest feedback.
</div>
A few weeks ago we wrote a series of articles about ENS+IPFS websites (now removed). We even stored our blog in this method,

A lot happened in those few weeks. 

ENS replaced its (cumbersome) auction model with a renting one. You now simply pay 5$ per year for each name. The project also switched to a permanent registrar. 

We looked at the main resolver (where most ENS transactions are done). It seems that people connect ENS names their wallet, but not to their website. 

We got curious, how popular are ENS+IPFS websites? Well, Let's find out.

## Results: ENS+IPFS websites
We found the following list of ENS+IPFS websites (in no particular order).

- [almonit.eth](http://almonit.eth) (**that's us!**)
- [pepesza.eth](http://pepesza.eth) (**that's one of our developers!**)
- [portalnetwork.eth](http://portalnetwork.eth)
- [monkybrain.eth](http://monkybrain.eth)
- [amoebacore.eth](http://amoebacore.eth)
- [hozt.portalnetworkweb.eth](http://hozt.portalnetworkweb.eth)
- [christophershen.eth](http://christophershen.eth)
- [phyrextsai.eth](http://phyrextsai.eth)
- [mycrypto.dappnode.eth](http://mycrypto.dappnode.eth)
- [game.portalnetwork.eth](http://game.portalnetwork.eth)
- [cv.gnelson.eth](http://cv.gnelson.eth)
- [digitallyrare.eth](http://digitallyrare.eth)
- [neelyadav.eth](http://neelyadav.eth)
- [mattcondon.eth](http://mattcondon.eth)
- [nathanclayforcongress.eth](http://nathanclayforcongress.eth)
- [bradsherman.eth](http://bradsherman.eth)
- [liquid-long.keydonix.eth](http://liquid-long.keydonix.eth)
- [liquid-close.keydonix.eth](http://liquid-close.keydonix.eth)
- [hadriencroubois.eth](http://hadriencroubois.eth)
- [badger.merklework.eth](http://badger.merklework.eth)
- [pricefeed.doracle.eth](http://pricefeed.doracle.eth)

You can access them using status or opera browser for mobile. 

Even better: you can write us (contact@almonit.club) to become an early testers of Almonit ENS+IPFS plugin (will be published soon). The list is already embbeded inside the plugin! 

## Investigation methods
ENS uses a contract called resolver to connect names to content. While you can create your own resolver, most people (we believe) use the resolver that ENS team provides.

We scanned only the latest version of the ENS resolver. This means that there may be more ENS+IPFS websites hiding in old versions.

Our method was strightforward. We collected all the transactions that connected an ENS name to an IPFS respository. Then we checked if the repository is live. We kept only "serious" websites, and ignored those that look like a test.

Even in cases it was live, we still had a problem. ENS supplies the hash of a name, but not the registered name itself. 

This means that we had to reverse the hash somehow. It went very well for the websites so far, but we'll need help in the future to keep this index up-to-date.

## Help needed: unidentified ENS+IPFS websites
Here was supposed to be a list of unidentified ENS+IPFS websites. Alas, we were able to deduce all relevant ENS names. Cheers to us, I guess.

## Issues
The ENS+IPFS sphere is not developed, to say the least. There are less than 20 websites so far.

One issue is availability. Many ENS+IPFS websites are set in the registrar, but are not available in ipfs. Reminder: IPFS+ENS is not magic. Your website will be available if it's either popular or if you seed it yourself. 

There tools and service to make your website available. Either for free using [this tool](https://github.com/agentofuser/ipfs-deploy) (up to approximately 1 GB by Infura, Pinata or Cloudflare). Or for a price, check out Pinata and Eternum.

Gateways are actually another (strange) issue. 

Some websites are available in one gateway, but not in another. Ain't ipfs supposed to be a p2p network? where if one (strong) node like a gateway has content, all the others should have it? strange indeed.

That said, ENS+IPFS is a cool idea. What's more romantic than being a real pioneer in a novel technology? It's like being in the first wave of Mars settles.

There are use-cases for every new technology, it's up to us to find the use-cases for distributed websites.

