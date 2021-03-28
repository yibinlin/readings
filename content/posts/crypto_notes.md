---
title: "Crypto Notes"
date: 2021-03-27
# weight: 1
aliases: ["/crypto"]
tags: ["crypto"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true
hidemeta: false
hideSummary: true
comments: false
description: "Notes to follow recent trend in Crypto"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
searchHidden: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page

---


## BlockChain Scalability problems

- [Nice Summary on Wikipedia](https://en.wikipedia.org/wiki/Bitcoin_scalability_problem)
- E.g. Bitcoin can only process around 7 transactions (tx) / sec.
- Limited by block size
- Hard fork like Bitcoin cash to increase the block size.
- Soft fork like Seg Wit (both old and new nodes can still run on the same blockchain)
- "Layer 2" systems like [Lightning Network](https://en.wikipedia.org/wiki/Lightning_Network)
  - creates channel on the worker nodes to send payments
  - if users don't follow the channel payment, penalty is that the payment will be lost.
  - when channel closes, the final transaction will be broadcast to the chain.
  - Seems to work, but so far low adoption. (Since 2018, 3 years)

## Theta Network

- Watch TV (has to be in a website within their network... Their website experience is not as good as Youtube), then you become a node in CDN and then you earn `TFuels` (their unlimited token, i.e. subject to inflation).
  - They have a non-inflation (fixed total number) token called Theta token, which governs the issurance of `Tfuel`s (also PoS).
- Steve Chen (Youtube co-founder, ex-Paypal) is an advisor - doesn't seem to be an investor.
- [Theta TV Link](https://www.theta.tv)

## DeFi (Decentralized Finance)

- MakerDAO: lending platform, pegged to US dollar.
- Smart Contract for enforcible terms..
- Current stage: open source code can be copied, getting competitors easy..
- Not compliant with KYC and AML (Anti- Money Laundering).
- Collaterol requirements for "virtual" stock trading not required (for now?)
