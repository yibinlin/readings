---
title: "(Basic) Docker Notes"
date: 2021-03-19
# weight: 1
# aliases: ["/first"]
tags: ["docker", "engineering"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true
hidemeta: false
hideSummary: true
comments: false
description: "Docker Notes just to help me understand and use it to do things I want."
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

## History

- Docker was originally built on top of lxc, but later dropped the dependency.
- now uses `libcontainer` other than `liblxc`
- Solomon Hykes' [own answer](https://stackoverflow.com/questions/17989306/what-does-docker-add-to-lxc-tools-the-userspace-lxc-tools) in 2013 about Docker vs. lxc.
- > `libcontainer` is Docker's own library of accessing namespace and cgroups, etc.

## Stopped Containers

- My guess is that the process is stopped, but the namespace and cgroups, etc. are still saved in case the container can be (re-)started later.

## Docker Container inside a Docker Container

- Can do it (as a feature);
- Not recommended in most cases.
  - Instead, [Start a sibling container by mounting the Docker socket into the container](https://stackoverflow.com/questions/27879713/is-it-ok-to-run-docker-from-inside-docker)

## Data Persistency
- [Official Doc](https://docs.docker.com/storage/)
- > By default all files created inside a container are stored on a writable container layer. 
  - So data is not persisted by default after the container is removed.
