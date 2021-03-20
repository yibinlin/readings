---
title: "Airflow Study Notes"
date: 2021-03-17T11:30:03+00:00
# weight: 1
# aliases: ["/first"]
tags: ["airflow", "engineering"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: false
hideSummary: true
comments: false
description: "Study Notes about Airflow."
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

## 1. Environment

- Vagrant: create and configure lightweight, reproducible dev environments (local Kubernetes cluster)

## 2.1 Basics

### 2.1.1 Concepts

- Operator: describes a single task in your data pipeline.
- Task: an instance of an operator
- Workflow: everything defined in Airflow.

### Architecture

- ![architecture diagram](../airflow_architecture.png)

## 2.2 Installation

- Using docker
  - Docker mysterious image tags, e.g. [slim, buster, etc.](https://stackoverflow.com/questions/54954187/docker-images-types-slim-vs-slim-stretch-vs-stretch-vs-alpine)
  - `buster` is Debian release names, makes sense..
  - `Alpine Linux` is a [distro](https://www.reddit.com/r/linux/comments/3mqqtx/alpine_linux_why_no_one_is_using_it/):
    - > The Alpine Docker image is extremely popular as it is only 5.5MB and includes a package manager with thousands of packages.
    - Uses `musl`, a relatively new C standard library (therefore occasional compatibility issues).
  - `Ctrl + D` to log out of current su'ed user.
  - Build the image: `docker build -t airflow-basic .`
    - Check with `docker image ls`
  - Run the image: `docker run --rm -d -p 8080:8080 airflow-basic`
    - `--rm` means Automatically remove the container when it exits.

## 2.3 Airflow UI

- Stop the current docker `docker container stop [Container ID]`
- Start new container: `docker run -p 8080:8080 -d airflow-basic`
- To see stopped containers: `docker ps -a | grep Exit`

## 2.4 Airflow CLI

- `airflow initdb`: do it at start, or after you change the metadata DB.
- `airflow resetdb`: reset metadata
- `airflow upgradedb`: upgrades to the latest version.
  - The same as `airflow initdb` after the first run
- `airflow webserver -p [port] -w [num_workers]`: webserver instance
- `airflow scheduler`
- `airflow worker`

## 2.5 DAGs and CLI

- `airflow list_dags`
- 
