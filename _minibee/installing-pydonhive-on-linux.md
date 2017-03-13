---
title: Installing pydonhive on Linux
summary: how to install the hive (pydongui) on Linux
layout: documentation
type: guide
date: 2017-02-06
category: software
subcategory: installation
tags:
    - basics
---

# Installation

{% include pydonhive_installation_short_linux.md %}


## Alternatively:
Do the following all in the terminal:

    wget https://github.com/sensestage/ssdn_python/archive/master.zip
    unzip master.zip
    cd ssdn_python-master/
    sudo ./installation.sh


{% include dependencies_pydonhive.md %}

{% include packagecontents_pydonhive.md %}


# Installation step by step

{% include pydonhive_installation_0.md %}

On Linux you can usually find this in a menu like “Utilities”, and in some window managers if you press [ctrl]+[alt]+[t] it brings up a terminal window. Some file browsers also have shortcuts to open a terminal at a specific location.

## [step 1] : unpack the package

{% include pydonhive_installation_1.md %}

On Linux in the file manager there is usually a plugin to extract them.

## [step 2] : check Python version

{% include pydonhive_installation_2.md %}

## [step 3] : Install setuptools

{% include pydonhive_installation_3.md %}

Most Linux distributions also provide setuptools in their package manager, e.g. on Debian/Ubuntu you can install it with:

    $ sudo apt-get install python-setuptools

## [step 4] : Install the dependencies (from the pydon package you downloaded):

{% include pydonhive_installation_4.md %}

## [step 5] : Pydon

{% include pydonhive_installation_5.md %}

# Starting the program

{% include pydonhive_start.md %}
