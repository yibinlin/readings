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

### 2.4.1 DAGs and CLI

- `airflow list_dags`
- `airflow trigger_dag`
- `airflow list_tasks`
- `airflow list_dag_runs`
- `airflow test [DAG_ID] [TASK] [Execution_date]`

## 3.1 First DAG

### 3.1.1 Docker

- Avoids debugging process while installation..
- Because it is standardized, and isolated process.

## 4 Following Official Tutorial

Following official tutorial using `docker compose` other than local installation.

### 4.1 Specific Issues Encountered in Current Version (2.0.1)

1. Error: WARNING - Exception when importing 'airflow.providers.microsoft.azure.hooks.wasb.WasbHook' from 'apache-airflow-providers-microsoft-azure' package: No module named 'azure.storage.blob'
    - Solution [here](https://github.com/apache/airflow/issues/14266)
2. Error: (webserver already started at PID ...)
    - killall -9 airflow
3. Error running `backfill` Airflow command
    - Found issue discussion [here](https://github.com/apache/airflow/issues/14379)
    - Changing image to python 3.8 version will fix it (originally it was a python 3.6 image)


## 4.2 General Issues

1. Error: webserver exited with 137
    - Increase your Docker memory configuration..

## 4.3 Notes (Learnings)

1. Flower (container)
    - web based tool for monitoring and administrating Celery clusters. 
2. Creating a new DAG: DAG name is NOT the file name, it is defined in Python Dag code param..
    - Similar issue [here](https://stackoverflow.com/questions/45534535/airflow-not-loading-dags-in-usr-local-airflow-dags)
3. DAG `execution date`
    - The `execution date` is not the actual DAG run date (there is a DagRun `start date` and `end date` for that)
    - `execution date` is normally DagRun `start date` - `schedule_interval`, which is the start time of the data being processed (think of ETL)
    - Can use `{{ ds }}` to find execution date (may not be the same as the `date` command result, which is the actual current date)
4. Backfill task “deadlocked”
    - It means the Backfill task `execution date` is later than `Dag end date` of the Dag (defined in Dag definition, note this is not a `DagRun end date,` which is tied to a specific DagRun), or is in the future
5. Triggering a task
    1. Cannot trigger a task earlier than its `Dag start date` (defined in Dag, not in a specific Dagrun)
        - Example error message `The execution date is 2021-04-06T00:00:00+00:00 but this is before the task's start date 2021-04-16T00:00:00+00:00.`.
    2. Can trigger a task between `Dag start date` and `Dag end date`.
    3. Cannot trigger a task with the same timestamp (up to second) as an existing task that happened before (you should `clear` that usually):
        - Error message: `Key (dag_id, execution_date)=(tutorial2, 2021-04-16 00:00:00+00) already exists.`
        - However, you can trigger another manual task run even if it is only 1 second difference (e.g. at `2021-04-16 00:00:01+00`)
6. You can run Airflow command on a `scheduler`, `webserver` and even on a `worker`(?)
