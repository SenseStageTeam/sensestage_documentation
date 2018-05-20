---
title: Installing Pydon on Linux
summary: How to install Pydon on Linux

parent: Pydon Installation Guide
layout: guide
type: guide
guidestep: 2

creation-date: 2017-02-06
category: software
subcategory: installation
tags:
    - basics
---

# Installation

* Download the source: [Python client download](https://github.com/sensestage/ssdn_python) (choose the zip option, or use [this direct link](https://github.com/sensestage/ssdn_python/archive/master.zip))
* Unpack the package (double-click, or right-click menu “extract here”).
* Run the `./installation.sh` script that is in the package.


The commands to type should be similar to these:

```
    cd ~/Downloads/ssdn_python-master
    sudo ./installation.sh
    Password: *
```


> Note for Ubuntu users: you will need both the `python` and `python-tk` package installed from the package manager


{% include pydonhive/pydonhive_start.md %}
