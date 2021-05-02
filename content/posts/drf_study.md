---
title: "Django and Django REST Framework (DRF) Study Notes"
date: 2021-04-10
# weight: 1
# aliases: ["/first"]
tags: ["django", "drf", "django rest framework", "orm", "python"]
author: "Yibin Lin"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: true
hidemeta: false
hideSummary: true
comments: false
description: "Re: Django and Django REST Framework"
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

## Django Related

- Named after Django Reinhardt (Guitar Musician)
- Django has model - view - controller (also MVT, see blow)
- So it is sever side..
- [Flask vs. Django](https://data-flair.training/blogs/flask-vs-django/)
  - `Flask` is minimalist, can plug in other frameworks too.
  - `Django` binds a lot of things, including its own ORM system.
- Django: Model-View-Template form
- PHP vs. Django: not very compatible, I think PHP more logic is in the html page, and for Django the it is in the view (not template..)
  - [Django form example](https://www.geeksforgeeks.org/django-forms/) it shows MVT structure (insert some view content into the template to render forms).

## Django ORM

- QuerySet.delete():
  - Keep in mind that this will, whenever possible, be executed purely in SQL, and so the delete() methods of individual object instances will not necessarily be called during the process. If you’ve provided a custom delete() method on a model class and want to ensure that it is called, you will need to “manually” delete instances of that model (e.g., by iterating over a QuerySet and calling delete() on each object individually) rather than using the bulk delete() method of a QuerySet.
- JSONField
  - To be read..
- `F expressions`
  - can reference fields in the model as assigned value
- `exclude()` with multiple values:
  - Basically it is a negation logic. It is hard to explain, need to refer to [official doc](https://docs.djangoproject.com/en/3.2/topics/db/queries/#spanning-multi-valued-relationships)
  - different from `fliter()` with multiple values.
- How are the backward relationship (JOINS) possible?
  - it’s particularly important that all the models you’re using be defined in applications listed in INSTALLED_APPS. Otherwise, backwards relations may not work properly.
- Customize Django Manager:
  - Manager can add 1). more functions and 2). modify the initial QuerySet that the Manager returns
- Model methods:
  - just `self.xxx` methods in the table class (inherits `models.Model`)

## Django vs. DRF (Django Rest Framework)

- DRF: easier to write `views` for API endpoints.
  - And no templates, as there are no displayable pages.
