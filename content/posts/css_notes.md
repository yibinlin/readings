---
title: "Notes on CSS"
date: 2021-03-07
# weight: 1
# aliases: ["/first"]
tags: ["css", "engineering"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
hideSummary: true
comments: false
description: "Notes for my CSS study."
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


## General Guideline

- Try to re-build layout of other websites, as practice, etc.

## Flexbox

- [Flexbox cheat sheet](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- `justify-content` means alignment in the main axis.
- `align-items` means alignment in the cross axis.
- Difference between Flex and Grid: Flex is 1-dimensional (and one direction), while grid is for 2-dimensional formatting.

## BEM Naming Convention

- [BEM cheat sheet](https://css-tricks.com/bem-101/)
- [RSCSS](https://github.com/rstacruz/rscss) vs. BEM

## Grids

- Grids can overlap if it is explicitly set.
- z-index can also work on grid cells, changing the overlap order.
- the grid cell can be set to other display patterns, such as: `display: flex` and can be used to center the text vertically:
  - Look at this [StackOverflow Question](https://stackoverflow.com/questions/8865458/how-do-i-vertically-center-text-with-css#)
  - the grid cell can be a grid container too by declaring `display:grid`.
- Grid settings does not affect fixed-position elements.
  - Therefore we may need to have special empty sections for those fixed-position elements e.g. navigation header bars.

## CSS Transforms

- most used:
  - `translate()`
  - `scale()`
  - `rotate()` - means `rotateZ()` if only one parameter is given.
  - `skew()`
- 3D transforms with rotateX / Y

## CSS Transitions

- `transition: watch-value DURATION DELAY TIMING-FUNCTION (how to transit);`
- [Timing functions reference](https://easings.net/) with in-lie demos.
