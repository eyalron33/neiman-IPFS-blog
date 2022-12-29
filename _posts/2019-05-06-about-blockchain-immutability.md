---
layout: post
title: About Blockchain Immutability 
category: Theory 
comments: true
description: A discussion about blockchain immutability myth including a suggestion for immutability model for blockchains 
tags:
    - Immutability
---
## Introduction

Immutability is an inseparable characteristic of blockchains. Every blockchain promises immutability. Some implicitly, as in Bitcoin where Satoshi Nakamoto [mentions](https://bitcoin.org/bitcoin.pdf) “transactions that are computationally impractical to reverse”. Others explicitly, as in the case of [Steem](https://steemit.com/steem/@m0se/steem-is-immutable-think-twice-before-you-post-you-can-t-delete-later-on), or most famously, [Ethereum](https://github.com/ethereum/wiki/wiki/White-Paper).

Recent events, namely, several Ethereum hard forks, raised myriad discussions, [some of them](https://www.reddit.com/r/ethereum/comments/59naa2/what_does_immutability_really_mean/) driven by pillars of the community, making it clear that there is a lack of clarity and consensus about what immutability is.

Ethereum classic, which was created in the wake of Ethereum’s DAO hardfork (see details below), [based](https://ethereumclassic.github.io/) its philosophy around immutability. Failing to phrase it accurately led to experts, such as Princeton’s associate professor Emin Gün Sirer, [criticising](https://twitter.com/el33th4xor/status/820296557836701697) Ethereum Classic for repeatedly violating the immutability they brag of.

We provide here a more precise definition of immutability. This is an essential step in the development of blockchains, as it is impossible to expect a blockchain to be immutable without first precisely defining this term.

As an example, we rephrase Ethereum Classic’s immutability principles in our terminology.

We define two types of immutability.

1.  **Immutability of History (IoH)** ensures transaction finality by demanding immutability of past consensus, i.e. that the consensus about the longest chain at past time points will not change.
2.  **Immutability of Process (IoP)** protects against irregular transactions or changes to the scripting language by demanding that the definition of valid blocks and chains will not change.

Since complete adherence to IoP may result in stagnation of a blockchain, we later on divide its possible violation to four types; some of them may be considered as positive violations of IoP (such as fixing bugs or adding features).

The word “immutability” may be misleading, as in practice any change to a blockchain can be made if a large enough consensus is achieved.

Hence, what we establish in this text is not a tool to improve blockchains’ security, but rather a concept to improve blockchains designers clarity. We hope that future white papers will clearly specify which type of immutability they aim for, and which type of immutability, if any, is breached with each fork.

But first we begin with some history, explaining the roots of the immutability discussion.

## The Roots of the Blockchain Immutability Myth

In the initial wave of blockchain enthusiasm, people bestowed upon the technology properties it does not have.

The fact that a transaction cannot be reversed by a centralized body formed into “transaction cannot be reversed, period” (which is false). The fact that proof of work validity is backed by a mathematical proof turned into “blockchain validity is backed by mathematical proofs” (again, false).

Add to this the fact that this futuristic technology was invented by the mysterious Satoshi Nakamoto (with further development by the equally mysterious [Nicolas van Saberhagen](https://monero.stackexchange.com/questions/162/what-is-known-about-nicolas-van-saberhagen) or [Tom Elvis Jedusor](https://motherboard.vice.com/read/lord-voldemort-tom-elvis-jedusor-is-trying-to-save-bitcoin-mimblewimble)) which made blockchains seem more like science fiction’s [Big Dumb Object](https://en.wikipedia.org/wiki/Big_Dumb_Object) concept than just another human invention.

The implicit Big Dumb Object misconception held as long as there were no major blockchain protocol scandals. But then came the DAO saga, shattering this comparison.

## The DAO Incident and the War on Immutability

The DAO (Distributed Autonomous Organization) was a project run on top of Ethereum’s blockchain. Slock.it, the creator of The DAO, collected around 150 million dollars (in the form of Ethereum) from the public, and let The DAO’s smart contract manage it. The project was Ethereum’s flagship, where Ethereum’s inventor, Vitalik Buterin, [proclaimed](https://twitter.com/vitalikbuterin/status/741176077435973632) that in a few months The DAO would turn into a liquid democracy.

That’s when things went wrong. Drastically wrong.

The DAO smart contract had a few bugs, and on the morning of the 17th of June 2016, a malicious attacker abused one of them to steal 60 million dollars (in terms of Ether).

This hack had nothing to do with Ethereum’s blockchain immutability. The DAO was not a blockchain, but rather a project using Ethereum’s blockchain. The hack was not “cheating” the blockchain, but abusing a bug in The DAO’s code. It was similar to Bitcoin’s infamous Mt. Gox accident: badly written code was abused to hack a system and steal funds from its users.

The thing that destroyed the immutability of Ethereum’s blockchain was the subsequent hard fork. The hard fork introduced irregular transactions, taking the stolen funds from the hacker’s hands. Following the acceptance of the hard fork, [Bitcointalk](https://bitcointalk.org/) forum was filled with immutability discussions. A [Wikipedia war](https://bitcointalk.org/index.php?topic=1575487.msg15935700#msg15935700) on how to define a blockchain began.

Some claimed that immutability was not breached, as the blocks were not changed, but merely irregular transactions were introduced. Others disagreed, claiming that immutability is also about the process, and not only the history. The discussions led to Gavin Wood, Ethereum’s co-founder and the author of Ethereum’s specifications, asking publically, “[what does immutability really mean](https://www.reddit.com/r/ethereum/comments/59naa2/what_does_immutability_really_mean/)?”

The DAO hard fork [was](https://bitcointalk.org/index.php?topic=1575487.msg15833662#msg15833662) different from all others that occurred before. It obviously surprised many, who thought that such a thing was impossible. To understand the root of the surprise, we have to distinguish next between two similar-but-different terms.

## Between Improbable and Extremely Hard

There are a few attack vectors on Bitcoin.

One is double spending via majority of hash power. If you have 51% of the network’s computational power (in some scenarios, even slightly less), you can make a big transaction, get the reward once it’s mined, and then use your superior computational power to create a new longer chain which doesn’t have this transaction.

Will it work? [Bitcoin’s hash power](https://blockchain.info/charts/hash-rate) stands at the end of February 2017 at more than 3,000,000 TH/s, which means that you’ll need at least 215000 units of one of the [strongest miner](https://www.hobbymining.com/mining-hardware/) (Antminer S9, 14 TH/s, 2100 dollar a piece), costing around 450 million dollars. That’s before calculating the electricity in, and the fact that this is an upper bound on the miners capabilities. Possible? Yes. Hard? Extremely.

The second attack vector is changing Bitcoin’s protocol. For this you need to write a modified client giving you extra coins, and then convince a large enough portion of the community to use your version. Remembering that it’s a community that has been arguing about block size for more than a year now shows that this way is not practical. Possible? Yes. Hard? Extremely.

A third attack vector is to brute force hack a private key. But that’s [not even physically possible](http://security.stackexchange.com/questions/25375/why-not-use-larger-cipher-keys/25392#25392). What you can do is try to guess the private key. But the number of possibilities is so large, which makes it very **improbable** that you’ll succeed. Actually, it is so improbable to guess a private key that some would argue that Bitcoin private keys are as strong as the laws of nature (which may themselves be high probability events and not really “laws” for all that we know.)

It is easy to confuse and project the private key immutability upon all of the other attacking vectors. But in reality, it is just not the case. Blockchains can be hacked, but it’s just extremely hard in general. Though, as the DAO hard fork demonstrated, it may not even be that difficult to do under certain circumstances.

## Defining Immutability

Time for the big question, what does immutability mean?

In Java or Rust programming languages, for example, Immutability is a design pattern, describing “an object which cannot be modified by the code of the program after it is first assigned a value”. Is this absolute immutability? No. The object can be changed from outside the program by the system operator.

Actually, the same is true for any centralized system: if the operator controls the memory directly, then nothing is really immutable. In a distributed system this is allegedly solved, since there is no central operator. However, there we encounter a much different problem (the Byzantine Generals’ Problem) : **which value** is immutable? Each node may store a different value, so exactly which value is it that we want to be immutable?

Blockchains solve this problem by defining a method of determining the state of a distributed system at a specific point in time. Intuitively then, immutability may be the expectation that a state cannot be changed after it has been determined by the system, and that the process of determining the state cannot be changed.

We define these accurately for blockchains containing the following components (a full formal definition of a blockchain is beyond the scope of this text):

1.  A collection of linked blocks, including at least one genesis block (i.e. with no parents).
2.  A validation function taking a chain of linked blocks beginning from a genesis block and returning whether it is a valid chain or not.
3.  A consensus protocol defining what the “main chain” is in the collection of blocks (in Bitcoin, for example, it is the one demonstrating the most hash power).
4.  A depth-standard, **D**, specifying which block depth in a main chain is enough in order for users to consider it as part of the main chain (in Bitcoin, for example, the standard is six confirmations).

This leads us to the following specification of the two types of blockchains defined at the beginning:

<span style="color: #333300;">**Immutability of History (IoH)**: If a block _B_ has height _H_ (i.e., there are _H_ blocks proceeding it) and depth deeper than **D** (i.e, there are at least **D** blocks after it) in the main chain at some time _T_, then the main chain will contain _B_ at any time later than _T_, and the height of B will always be equal to H.</span>

IoH both demands the consensus protocol be safe enough such that if a block reached a certain depth, it would be included in the main chain at all future times, and that the consensus protocol be changed only if it does not influence past states. In addition it is specified that the height of _B_ is always _H_ in order to make it impossible to add blocks before block B.

IoH is what most users understand, intuitively, when they speak of blockchains being immutable. It is this immutability that provides transactions finality.

<span style="color: #333300;">**Immutability of Process (IoP)**: The validation function may not be changed.</span>

IoP disqualifies irregular transactions or unexpected blockchain behavior over time. However, since it also disqualifies positive changes, such as improvement of the protocol, it will often be violated. We classify possible violations according to four types.

1.  **Removing a bug**. This means removing options from the validation function. An example is [Ethereum’s hardfork](https://blog.ethereum.org/2016/10/13/announcement-imminent-hard-fork-eip150-gas-cost-changes/), in which the creation of empty accounts was disallowed.
2.  **Adding a feature.** It is impossible to think of all needful blockchain features in advance. An example is [SegWit](https://bitcoincore.org/en/2016/01/26/segwit-benefits/).
3.  **Fixing a bug.** Similar to ‘A’, but here a feature is fixed, not removed. An example is [Ethereum’s gas costs changes](https://blog.ethereum.org/2016/10/13/announcement-imminent-hard-fork-eip150-gas-cost-changes/).
4.  **One-time actions.** For example, irregular transactions.

Finally, note that _irregular transactions are often equivalent to violating immutability of history_. If the blockchain contains a transaction from A to B, and an irregular transaction from B to C is added, it is equivalent to reversing the valid transaction from A to B and adding an irregular transaction from A to C.

## The Ethereum Classic Code of Principles – Rephrased

In the wake of Ethereum’s DAO hard fork, a new coin came to life. It continued Ethereum’s unforked chain, where the DAO’s money remained in the hands of the hacker. Some of its proponents claim that it is the original and true Ethereum blockchain.

The main selling point of Ethereum Classic was its immutability. They phrased their “code of principles” in a [declaration of independence](https://ethereumclassic.github.io/assets/ETC_Declaration_of_Independence.pdf) publication, but the document certainly had problems phrasing it in a satisfactory manner. While the more technical phrasings were criticised by experts, the human phrasing (“no bailout hardforks”) was incomplete in light of some actions that the community took, namely, not following Ethereum’s example in deleting empty accounts from the blockchain.

Using our definition it is easy to phrase “Ethereum Classic’s code of principles” as follows:

_Ethereum Classic promises to never do a hard fork that violates IoH or a “one-time action” kind of violation to IoP that creates an “irregular transaction”. However, Ethereum Classic allows violation of other principles of IoP, if those improve the system._

## Conclusion and Clarity of Blockchains Design

If a blockchain were only about immutability, its technical state would have been frozen at launch. But such a governing model would lead to stagnation. A more practical approach, as with defensive democracy, is that a blockchain must guard itself, even against the occasional breach of immutability.

What we suggest is not utter immutability, but utter clarity. Specifically, we propose the following rules:

1.  A blockchain’s white paper must specify which immutability it aims to maintain, both within each of its versions, and across planned hard forks.
2.  A whitepaper must contain a protocol for forks which breach immutability. An example of this is Bitcoin’s 95% adoption. Lack of such a protocol leads to impromptu protocols, such as Ethereum’s [usage of carbonvote](https://blog.ethereum.org/2016/07/26/onward_from_the_hard_fork/) before the DAO hardfork (this ended up [being criticized](https://medium.com/@WhalePanda/what-happened-with-ethereum-eth-and-ethereum-classic-etc-3c69fc7cbb69#.su7oe2sc2)).
3.  In every unplanned fork, it must be specified if any immutability layers are breached.
4.  Each immutability breach must be clearly stated and justified.

In addition, forks which are predefined in the whitepaper (and hence are well-known in advance) should not be considered immutability-breaching.

While defining immutability may be seen as a grey task, it is in reality one of the most important things in designing blockchains.

Immutability is one of the main qualities that blockchains offer to replace and fix the traditional centralized institutes system. This immutability is saved by the consensus protocol and the community, and hence it must be accurately understood by the creators, managers and users of each blockchain which immutability they aim to achieve.

Ignoring accurately defining immutability beforehand will almost surely end in community disputes and possible splits further down the road. As members of the blockchain community, we must all strive to avoid this.

Please keep that in mind the next time you work on a whitepaper.

**[Written by Eyal Ron and Craig Sailor, with additional valuable input by Dr. Simone Wurster]**
