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
- `docker start [CONTAINER_ID]` can start the container with the initial setting, e.g. the network port bindings.

## Docker Container inside a Docker Container

- Can do it (as a feature);
- Not recommended in most cases.
  - Instead, [Start a sibling container by mounting the Docker socket into the container](https://stackoverflow.com/questions/27879713/is-it-ok-to-run-docker-from-inside-docker)

## Data Persistency

- [Official Doc](https://docs.docker.com/storage/)
- > By default all files created inside a container are stored on a writable container layer.
  - So data is not persisted by default after the container is removed.

## Docker Container Main Process (`ENTRYPOINT` or `CMD`)

- [Doc](https://docs.docker.com/config/containers/multi-service_container/)
  - > The container’s main process is responsible for managing all processes that it starts. In some cases, the main process isn’t well-designed, and doesn’t handle “reaping” (stopping) child processes gracefully when the container exits. If your process falls into this category, you can use the --init option when you run the container. The --init flag inserts a tiny init-process into the container as the main process, and handles reaping of all processes when the container exits.
- So, the main process is the root process for a container I think..

## DockerFile

- [Example, Illustrated by Marc Lamberti](../example_docker_file.txt)

## Docker Compose

- vs. Kubernetes?
  - Kubernetes can run on multiple hosts
  - Docker Compose is usually one machine (?)
- Kubernetes vs. Mesos?
  - Sounds like Mesos are doing multi-host deployment (not only containerized)
  - Kubernetes focses in containerized deployment (it supports other containers than Docker too).

## Troubleshooting

- Docker container finishes with exit code 137:
  - It is related to memory, you may want to increase your Docker memory configuration.
  - details [here](https://www.petefreitag.com/item/848.cfm)
