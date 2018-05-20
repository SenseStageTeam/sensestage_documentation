---
title: Installing Pydon the Hard Way on OSX/Linux
summary: Describes step-by-step what the installation script is doing if you want to do it yourself, or need to debug the process.
layout: guide
type: guide
guidestep: 0
level: intermediate
priority: 50

creation-date: 2017-02-06
category: software
subcategory: installation
tags:
    - basics
---

# Installation Dependencies

{% include pydonhive/dependencies_pydonhive.md %}

# Installation step by step

{% include pydonhive/pydonhive_installation_0.md %}

On OSX you can find the program `Terminal` in the `Applications` folder, in the folder `Utilities`. Or with the Spotlight search.

On Linux you can usually find this in a menu like “Utilities”, and in some window managers if you press [ctrl]+[alt]+[t] it brings up a terminal window. Some file browsers also have shortcuts to open a terminal at a specific location.

## [step 1] : unpack the package

{% include pydonhive/pydonhive_installation_1.md %}

On OSX you can just doubleclick on them to extract them.

On Linux in the file manager there is usually a plugin to extract them.


## [step 2] : check Python version

{% include pydonhive/pydonhive_installation_2.md %}

## [step 3] : Install setuptools

{% include pydonhive/pydonhive_installation_3.md %}

Most Linux distributions also provide setuptools in their package manager, e.g. on Debian/Ubuntu you can install it with:

    $ sudo apt-get install python-setuptools


## [step 4] : Install the dependencies (from the pydon package you downloaded):

{% include pydonhive/pydonhive_installation_4.md %}

## [step 5] : Pydon

{% include pydonhive/pydonhive_installation_5.md %}

# Starting the program

{% include pydonhive/pydonhive_start.md %}
