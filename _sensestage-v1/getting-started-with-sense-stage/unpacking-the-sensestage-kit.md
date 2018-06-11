---
title: Unpacking the Kit
summary: A guide on what is in the Sense/Stage kit.
layout: guide
type: guide
parent: Getting Started with Sense/Stage
guidestep: 1

creation-date: 2017-02-06
tags:
    - basics
    - todo
category: introduction
subcategory: getting-started
---


To begin with, you should make sure you have all the necessary hardware for running a Sense/Stage network. If you purchased a kit, this is the time to inspect the contents of your kit and be able to identify the various parts of the Sense/Stage hardware setup.

Your starter kit should include the following:

1. 2 MiniBee boards including female angled headers
2. 3 XBee radios (all but one connected to MiniBees)
3. a red coordinator board
4. 2 green Xpee expansion boards including male angled headers
5. 2 green Xpree expansion boards including male angled headers

There are a few things not included in the kit that you will need to purchase separately:
1. A USB mini cable to connect the coordinator board to your computer
2. LiPo batteries to power the MiniBee boards (one for each)
3. A battery charger to charge your LiPo batteries

> See [Battery and Charger](#battery) for more information on the battery requirements of the MiniBees

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

> [More information about the coordinator board](/sensestage-v1/coordinator-board)

# Expansion Boards

Every starter kit comes with expansion boards for adding new sensors and custom circuits to your MiniBees. There are two types of expansion boards: the standard **XPree** experimentation board, and the simplified **XPee**.

You should have one XPree and one XPee for each MiniBee in your kit.

![](/img/minibee-expansion-kit-small.jpg)

> [More information about the expansion boards](/sensestage-v1/expansion-boards)


# Battery and Charger {#battery}

You will need a [3.7 volt LiPo battery with a JST-PH 2mm connector](https://www.floris.cc/shop/en/lithium-ion-polymer-battery-extra-s/1168-lithium-ion-polymer-battery-37v-500mah.html) to power each MiniBee, as well as a charger board to charge these batteries. The batteries and charger are not included in the standard Sense/Stage starter kit, so you will have to purchase them separately.

We recommend the [Sparkfun LiPo charger basic](https://www.floris.cc/shop/en/lithium-ion-polymer-battery-extra-s/484-lipo-charger-basic-micro-usb-.html), but other LiPo chargers with the JST-PH 2mm connector will work just as well. You also will need to purchase an appropriate USB cable to connect the charger to a power source.


![](/img/lipo-polymer-battery-37v-500mah.jpg)
*LiPo battery with JST-PH 2mm connector*

![](/img/lipo-charger-basic-micro-usb.jpg)
*Sparkfun LiPo charger basic (USB cable not included)*

> NOTE! Make sure to fully charge your batteries before the first use.

> WARNING! LiIon batteries require special handling care. For more information see [this guide on using LiPo batteries with Sense/Stage](/sensestage-v1/guide-to-batteries/)
