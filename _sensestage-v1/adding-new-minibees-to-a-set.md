---
title: Adding new MiniBees to a set
summary: A guide on what you need to do when you add new MiniBees to a set that you already have
layout: documentation
type: guide
parent: adding-new-minibees-to-a-set
step: 0
featured-image: feature-thumb.jpg
creation-date: 2017-02-06
tags:
    - basics
    - todo
category: introduction
subcategory: getting-started
related:
    - Overview of the system
    - Unpacking the Sense/Stage MiniBee Kit
    - Install the Hive Software
    - Using X-CTU to configure an XBee
    - Using X-CTU to change settings of an XBee
    - Connecting a MiniBee for the first time
---

If you have bought a set of MiniBees in the past and now want to add more MiniBees to the same network there are a couple of things you need to do to make them function together in the same set:

- the new MiniBees (revision F) are shipped with the latest firmware. That means that you may need to install the latest version of the Hive software.
- the old MiniBees (whichever revision you had) can keep the firmware they have. The Hive software is aware of the different features of different versions of firmware. Of course, you can still choose to update the firmware to the latest version with the **Arduino IDE**, but this is *optional*.
- the XBee that is on your new MiniBee will be preprogrammed with a default channel and pan id.
- the new MiniBee needs to be added to the hive configuration.


# Updating the HIVE software

Updating the hive software means that you have to install the latest version: [follow the guide to install the hive software](install-the-hive-software).

# Adapting the channel and pan ID of the new XBee

The `channel` determines on which radio frequency the XBee are transmitting. The `pan id` is an identifier within the channel to distinguish different XBee networks from each other. XBees will just ignore traffic that is happening with different pan ids.


## Check the channel and pan id of your existing set

Connect your coordinator node with XBee on top to your computer. Follow the instructions to [read the settings](using-x-ctu-to-read-settings-of-an-xbee) of your XBee. Note down what the setting is of CH and ID.

![](/img/x-ctu-radio-settings-channel-panid.png)

## Configure the channel and pan id of the new XBee

Now that you know which `channel` and `pan id` your set is working at, you have to configure the new XBee to use that same `channel` and `pan id`.

- Take off the XBee from the coordinator node and put it aside.
- Take off the XBee from the new MiniBee and put it on the coordinator node.
- Follow the instructions to [change settings of an xbee](using-x-ctu-to-change-settings-of-an-xbee) and program the channel and pan id onto them.
- Repeat these steps for each of the new XBees that you have and want to add to the set.
- Once you are done with all the XBees, put the XBees back on top of the MiniBees and put the XBee that was orginally on the coordinator node back onto it.

# Add the new MiniBees to your hive configuration file

Now that the XBees are configured you can configure your MiniBee just like when you [connect a MiniBee for the first time](connecting-a-minibee-for-the-first-time).

# (Optional) update the firmware of your old MiniBees

**TO ADD**


# To do

- add instructions for updating the firmware of old minibees
