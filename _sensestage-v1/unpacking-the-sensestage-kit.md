---
title: Unpacking the Sense/Stage MiniBee Kit
summary: A guide on what is in the Sense/Stage MiniBee kit.
layout: documentation
type: guide
parent: unpacking-the-sensestage-kit
step: 0
featured-image: feature-thumb3.jpg
creation-date: 2017-02-06
tags:
    - basics
    - todo
category: introduction
subcategory: getting-started
related:
    - MiniBee
    - Expansion boards
    - Battery charging
    - Battery handling
---


To begin with, you should inspect the contents of your kit. Be able to identify the various parts of the Sense/Stage MiniBee hardware setup. Your starter kit should include the following:

1. 2 MiniBee boards including headers
2. 3 XBee radios (all but one connected to MiniBees)
3. a red coordinator board
4. 2 green Xpee expansion boards including headers
5. 2 green Xpree expansion boards including headers

You may have also purchased a battery kit, which should include 2 LiPo batteries and a red USB charging board.

![](/img/sensestagekit_annotated.png)


# MiniBees

These are the small sensor data capture devices that form the core of the Sense/Stage MiniBee system. If you're familiar with Arduino, then you're probably already accustomed to the kind of projects such devices can be used for.

Unlike an Arduino, the MiniBee has a built-in accelerometer and is ready to start measuring motion right out of the box.

In the future you'll likely want to add additional sensors to capture more phenomena of the physical world.

The standard Sense/Stage kit has 2 MiniBees. In addition, for each MiniBee you should have a black expansion header.

![](/img/minibee_revF_header_top.jpg)

# XBee Radios

While MiniBees can operate fine on their own as tiny Arduinos, their real power is in their ability to communicate data wirelessly over a distance.

In order to be able to engage in wireless communication, every MiniBee needs to be equipped with a little wireless radio device called an XBee.

All of your MiniBees will come with XBee radios already attached to them, labeled **N** for **NODE**.

You should also have one extra XBee to use with the coordinator board, labeled **C** for **COORDINATOR**.


*The right way of putting the XBee on the MiniBee:*
![](/img/minibee_revF_xbee_right.jpg )

*The **wrong** way of putting the XBee on the MiniBee:*
![](/img/minibee_revF_xbee_wrong.png)


# The Coordinator Board

The small red board with a mini USB connector on it. This board must also be equipped with an XBee radio. It will connect to your computer via USB so that your computer can join the wireless conversation with your swarm of MiniBees.

> NOTE: A USB mini cable is not included with your Sense/Stage kit!

## Putting the XBee on the Coordinator Board
Before you can use the coordinator board you need to connect an XBee to it. Your kit is provided with one extra XBee labled "C" for this purpose.

Be very gentle when attaching the XBee, and make sure you use the correct orientation.

*The right way of putting the XBee on the coordinator board:*
![](/img/coordinator_xbee_right.jpg)

*The **wrong** way of putting the XBee on the coordinator board:*
![](/img/coordinator_xbee_wrong.png)

> [More information about the coordinator board](coordinator-board)

# Expansion Boards

Every starter kit comes with expansion boards for adding new sensors and custom circuits to your MiniBees. There are two types of expansion boards: the standard **XPree** experimentation board, and the simplified **XPee**.

You should have one XPree and one XPee for each MiniBee in your kit.

![](/img/minibee-expansion-kit-small.jpg)

> [More information about the expansion boards](expansion-boards)


# Battery and Charger

If you also purchased a battery kit, you should find included two or five LiIon batteries and a red charger with a USB connector.

![](/img/usb-battery-charger-batteries.jpg)

> NOTE Make sure to fully charge your batteries before the first use.

> WARNING! LiIon batteries require special handling care. For more information see [this useful link](https://www.sparkfun.com/tutorials/241) from Sparkfun.com.

> [More information about the batteries](battery)
