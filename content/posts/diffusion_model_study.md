---
title: "Diffusion Model Study Notes"
date: 2024-02-10
# weight: 1
# aliases: ["/first"]
tags: ["misc", "diffusion", "stable diffusion"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
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


## Basic modules of Stable Diffusion Model

1. Basic tutorial: [https://comfyanonymous.github.io/ComfyUI_tutorial_vn/](https://comfyanonymous.github.io/ComfyUI_tutorial_vn/)
2. CLIP: encode text, another name: text encoder
3. Sampler: takes the main `Stable Diffusion` model as an input, takes both positive and negative prompts encoded by `CLIP` model + a latent image (can be blank)
    1. sampler takes this input latent image, adds noise to it and then denoises it using the main model
    2. prompts and negative prompts are passed to model at each sampling step
    3. sampler outputs the denoised image
4. VAE: translates an image from latent space to pixel space
5. Prompting: `(word:1.5)` means it is 1.5 more effective

## OpenArt

- OpenArt sharing workflows: [https://openart.ai/workflows/dev](https://openart.ai/workflows/dev)

## Installing ComfyUI

1. ComfyUI on Colab notebook:
    1. [https://colab.research.google.com/github/comfyanonymous/ComfyUI/blob/master/notebooks/comfyui_colab.ipynb](https://colab.research.google.com/github/comfyanonymous/ComfyUI/blob/master/notebooks/comfyui_colab.ipynb)
2. ComfyUI examples: [https://github.com/comfyanonymous/ComfyUI_examples/tree/master/2_pass_txt2img](https://github.com/comfyanonymous/ComfyUI_examples/tree/master/2_pass_txt2img)
3. ComfyUI installation locally
    1. Metal Performance Shaders (MPS)
    2. For Mac Metal: [https://github.com/comfyanonymous/ComfyUI?tab=readme-ov-file#installing](https://github.com/comfyanonymous/ComfyUI?tab=readme-ov-file#installing)
4. ComfyUI installation from Colab:
    1. Uses [CloudFlare Reverse Proxy](https://github.com/cloudflare/cloudflared)
