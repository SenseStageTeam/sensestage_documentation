---
title: Getting Started with Sense/Stage
summary: A guide to unpacking and setting up Sense/Stage for first time users.
layout: documentation
type: guide
date: 2017-02-06
tags:
    - basics
    - installation
    - todo
category: introduction
subcategory: getting-started
related:
  - anotherTitle
  - yetAnotherTitle
---

[0. Unpacking the Sense/Stage Kit](#step0)<br />
[1. Installing Software](#step1)<br />
[2. Plugging in and Turning On](#step2)<br />
[3. Getting your Hands on the Sensor Data](#step3)<br />
[3.1 Configuring the MiniBee](#step3.1)<br />
[3.2 Reading the Data](#step3.2)<br />
[4. Next Steps](#step4)<br />

# 0. Unpacking the Sense/Stage kit {#step0}

To begin with, you should inspect the contents of your kit. Be able to identify the various parts of the Sense/Stage hardware setup. Your starter kit should include the following:

1. 2 or 5 Minibee boards including headers
2. 3 or 6 Xbee radios (all but one connected to Minibees)
3. a red coordinator board
4. green Xpee expansion boards (2 or 5) including headers
5. green Xpree expansion boards (2 or 5) including headers

You may have also purchased a battery kit, which should include 2 or 5 LiPo batteries and a red USB charging board.

![](/img/minibee-starter-kit-labled.jpg)


## Minibees

These are the small sensor data capture devices that form the core of Sense/Stage. If you're familiar with Arduino, then you're probably already accustomed to the kind of projects such devices can be used for.

Unlike an Arduino, the Minibee has a built-in accelerometer and is ready to start measuring motion right out of the box.

In the future you'll likely want to add additional sensors to capture more phenomena of the physical world.

The standard Sense/Stage kit should have 2 Minibees, a PLUS kit has 5. In addition, for each Minibee you should have a black expansion header.

![](/img/minibee-single-kit.jpg)

## Xbee Radios

While Minibees can operate fine on their own as tiny Arduinos, their real power is in their ability to communicate data wirelessly over a distance.

In order to be able to engage in wireless communication, every Minibee needs to be equipped with a little wireless radio device called an Xbee.

All of your Minibees will come with Xbee radios already attached to them, labled **N** for **NODE**.

You should also have one extra Xbee to use with the coordinator board, labled **C** for **COORDINATOR**.


## The Coordinator Board

The small red board with a mini USB connector on it. This board must also be equipped with an Xbee radio. It will connect to your computer via USB so that your computer can join the wireless conversation with your swarm of Minibees.

> NOTE: A USB mini cable is not included with your Sense/Stage kit!

### Putting the Xbee on the Coordinator Board
Before you can use the coordinator board you need to connect an XBee to it. Your kit is provided with one extra XBee labled "C" for this purpose.

Be very gentle when attaching the Xbee, and make sure you use the correct orientation.

![IMAGE ILLUSTRATING ATTACHING THE XBEE WITH CORRECT ORIENTATION]()

## Expansion Boards

Every starter kit comes with expansion boards for adding new sensors and custom circuits to your Minibees. There are two types of expansion boards: the standard **XPree** experimentation board, and the simplified **XPee**.

You should have one XPree and one XPee for each Minibee in your kit.

![](/img/minibee-expansion-kit-small.jpg)


## Battery and Charger

If you also purchased a battery kit, you should find included two or five LiPo batteries and a red charger with a USB connector.

> NOTE Make sure to fully charge your batteries before the first use.

> WARNING! LiPo batteries require special handling care. For more information see [this useful link](https://www.sparkfun.com/tutorials/241) from Sparkfun.com.


# 1. Install the Communicator Software (aka. "The Hive") {#step1}

**The Hive** is a cross-platform program that allows you to read data streams coming in from the Minibees directly using OpenSoundControl (OSC). OSC is supported by virtually all interactive design software such as PureData, SuperCollider, Max for Live, Processing, Max/MSP, vvvv, and Isadora.

[Linux installation instructions](#install-linux)<br />
[OSX installation instructions](#install-osx)<br />
[Windows installation instructions](#install-win)<br />


## Installation on Linux {#install-linux}

### Download the installation package [here](https://github.com/sensestage/ssdn_python/archive/master.zip).

### Unzip the package
In the file manager: double-click, or right-click menu “extract here”.

### Run the installation script
Open a terminal and go to the directory where you unpacked the package. As root (using sudo) run the ./installation.sh script that is in the package.
    sudo ./installation.sh

> Note for Ubuntu users: you will need both the python and python-tk package installed from the package manager before running the installation script.

### Alternatively:
Do the following all in the terminal:

    wget https://github.com/sensestage/ssdn_python/archive/master.zip
    unzip master.zip
    cd ssdn_python-master/
    sudo ./installation.sh

### Start up the Hive ... (how?)

## Installation on OSX {#install-osx}

### Download the installation package [here](https://github.com/sensestage/ssdn_python/archive/master.zip)

### Unzip the package
In finder find the file you just downloaded and double-click it to unzip it.

### Run the installation script
Open up the Terminal application (you can find it in Applications/Utilities/ or do a Spotlight search for "Terminal").

Once your terminal is open, type "cd" followed by a space, and drag the folder you just unzipped from your finder into the terminal window. Hit enter.

Now type "sudo ./installation.sh" into the terminal and hit enter. Enter your password and hit enter again (you won't see it as you type, this is normal).

The commands I typed looked like this, yours should be similar:

    cd ~/Downloads/ssdn_python-master
    sudo ./installation.sh
    Password: *

### Run the Hive software ...

## Installation on Windows {#install-win}

### Download the software package for windows [here]()

### Download and install the Windows usb serial driver [here]()

### Install the latest python for windows using the msi installer (32 bit or 64 bit).
Just doubleclick and follow instructions, select to add python.exe to the path, otherwise just follow the default suggestions.

### Execute the install_pydon.bat file by doubleclicking

### Execute the start_pydon.bat file by doubleclicking to start pydongui



# 2. Plugging in and Turning On {#step2}

## Plug in the coordinator

## Turn on the Minibee

[Connecting a minibee](connecting-a-minibee-for-the-first-time)

# 3. See Data Coming In {#step3}

## 3.1 {#step3.1}

## 3.2 {#step3.2}


# 4. Going Forward


# TODO

- clean up
- use includes from other pages instead of duplicating information
