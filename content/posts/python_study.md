---
title: "Python Study"
date: 2021-05-01
# weight: 1
# aliases: ["/first"]
tags: ["python"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
hideSummary: true
comments: false
description: "Some more thoughts / learnings about Python"
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

## Python Type Projects

- A `type` object = an instance of `type` class = a normal class
  - `type` and `class` are interchangable since Python 2.4
  - `print(type(type)) # result: <class 'type'>`
  - `print(type(str)) # result: <class 'type'>`
  - So `type` class is also an instance of `type` class.
    - This is basica building block of Python, and cannot be expressed in Python language.
  - In python everything is an object, so a class is an object (instance) of `type`.
  - For details, see this [StackOverflow Post](https://stackoverflow.com/questions/55775218/why-is-object-an-instance-of-type-and-type-an-instance-of-object)
