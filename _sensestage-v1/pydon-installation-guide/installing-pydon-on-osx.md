---
title: Installing Pydon on OSX
summary: How to install Pydon on OSX

layout: guide
type: guide
parent: Pydon Installation Guide
guidestep: 1

creation-date: 2017-02-06
category: software
subcategory: installation
tags:
    - basics
---

<iframe src="https://player.vimeo.com/video/273863480" width="800" height="500" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>
<p><a href="https://vimeo.com/273863480">Sense/Stage: Installing on Mac</a> from <a href="https://vimeo.com/sensestage">Sense/Stage</a> on <a href="https://vimeo.com">Vimeo</a>.</p>

# Quick Installation

* Download the source: [Python client download](https://github.com/sensestage/ssdn_python) (choose the zip option, or use [this direct link](https://github.com/sensestage/ssdn_python/archive/master.zip))
* Unpack the package. In Finder find the file you just downloaded and double-click it to unzip it.
* Run the `./installation.sh` script that is in the package.
    * Open up the Terminal application (you can find it in Applications/Utilities/ or do a Spotlight search for "Terminal").
    * Once your terminal is open, type `cd` followed by a space, and drag the folder you just unzipped from your finder into the terminal window. Hit enter.
    * Now type `sudo ./installation.sh` into the terminal and hit enter.
    * The system will ask for your password. Enter your password and hit enter again (you won't see it as you type, this is normal).

    The commands to type should be similar to these:

```
    cd ~/Downloads/ssdn_python-master
    sudo ./installation.sh
    Password: *
```


{% include pydonhive/pydonhive_start.md %}
