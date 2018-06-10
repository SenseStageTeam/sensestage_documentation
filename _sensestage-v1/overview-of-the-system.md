---
title: Overview of the system
summary: This page gives an overview of the different components that are used in the system

layout: reference
type: reference

creation-date: 2017-02-06
category: introduction
subcategory: glossary
tags:
    - overview
    - introduction
status: complete
---

![]({{ base_url }}/img/v1/SenseStage-System.png)

The Sense/Stage MiniBee system has a number of components that are all interacting with each other.

# MiniBee

![The MiniBee]({{ base_url }}/img/minibee_revF_header_top.jpg)

This board is what Sense/Stage is all about. The MiniBee is a small microcontroller board that is designed to be paired with an [XBee radio chip](#xbee) to be used in Sense/Stage wireless sensing networks. The board itself is comparable to an Arduino, and can even be programmed with the Arduino IDE and used in almost exactly the same way.

The MiniBee has a built-in 3-axis accelerometer on board, so you can already start sensing movement right out of the box. The board also has a convenient pin-header which you can use to connect other sensors and actuators. We offer a number of [expansion boards](expansion-boards) that make it easier to hook up custom sensors while still keeping the size of your modules small.

Each MiniBee needs an [XBee radio](#xbee) attached to it for wireless communication to work. The radio chip must be programmed, along with all the other XBee radios in your network, to be on the same network ID and channel number. This is already done for you if you have purchased a kit.


# XBee {#xbee}

![The XBee]({{ base_url }}/img/xbee.jpg)

This is the wireless radio board made by the company [Digi](http://digi.com).

All the XBee radios in your Sense/Stage network have to be configured specially to work with Sense/Stage. There are special configuration profiles, available on our downloads page, that you will need to load on to your XBees before they can be used with Sense/Stage.

When you buy a MiniBee, or a MiniBee Kit, the XBees included are already pre-programmed with these profiles.

XBee radios are programmed using the program  [**X-CTU**](using-x-ctu-to-configure-an-xbee).

# Firmware

The firmware is the code that runs on the MiniBee and takes care of the communication with the [XBee](#xbee), reading out the sensors and driving the actuators, based on the configuration that is received. When you buy a MiniBee, it comes preprogrammed with:

* the [standard MiniBee firmware](basic-features-of-the-firmware) - which allows you to use the accelerometer and a lot of other sensors without having to program the MiniBee yourself
* a bootloader - which allows you to upload new firmware through the **Arduino IDE**, if you want to use customized firmware

The firmware is written in such a way that it communicates with the software that is provided for Sense/Stage.

# Coordinator node

There are two types of nodes in the Sense/Stage world: end-points, and coordinators. The coordinator is the node responsible for routing data between all the sensor nodes in your network, and there is usually only one. All of your sensor nodes are usually end-points - they gather sensor data and communicate it back to the coordinator so that you can do something with it.

The coordinator node is an [XBee radio chip](#xbee) connected via USB to your computer. Usually through an XBee programmer board like the [Sparkfun XBee Explorer USB](https://www.sparkfun.com/products/11812).

The coordinator node is the bridge between your sensor network and the Pydon software running on your computer.

![The coordinator node with an XBee on top]({{ base_url }}/img/coordinator_xbee_right.jpg)

# Pydon Software

A piece of software we wrote called [Pydon](getting-started-with-sense-stage/installing-pydon) handles the communication between your sensor network and your computer. You connect a coordinator node to your computer via USB, which in turn communicates with your sensor nodes.

Pydon is designed to work with a standard firmware that is pre-installed on the MiniBee boards.

Pydon communicates with other programs on your computer using Open Sound Control (OSC). For a complete list of OSC messages used by Pydon see the [OSC Messages reference page](osc-message-reference).
