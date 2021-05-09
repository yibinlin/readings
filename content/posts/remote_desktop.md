---
title: "Remote Desktop Setup"
date: 2021-05-09
# weight: 1
# aliases: ["/first"]
tags: ["misc", "remote desktop"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true
hidemeta: false
hideSummary: true
comments: false
description: ""
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

Recently I would like to connect to my home Desktop in LAN, just to do some work while I am at my other desk. It should be a mature and well-known technology but somehow I just (re-)discovered it..

## Connect to a PC from Mac OS

- In the Mac machine: use official software: `Microsoft Remote Desktop`, available in Mac OS App Store.
- In the PC:
  - Configure your PC to [allow incoming remote Desktop connection](https://docs.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-client-faq#how-do-i-set-up-a-pc-for-remote-desktop-).
  - I also marked my local WiFi network as a private network in my network configuration.
- Enter the local IP address of your PC
  - Probably you will need fixed local IP for your PC.
- The usual username and password
  - This is not correct: `username@PC-name` (although this is what )
  - This is correct: `username`
