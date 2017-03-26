---
title: Overview of the system
summary: This page gives an overview of the different components that are used in the system
layout: documentation
type: reference
creation-date: 2017-02-06
category: introduction
subcategory: glossary
tags:
    - todo
---

![]({{ base_url }}/img/SenseStage_overview.png)

The Sense/Stage MiniBee system has a number of components that are all interacting with each other.

# MiniBee

This is the core of the system: this board is what it is all about. The MiniBee is a small pcb with an Atmel microcontroller. It is comparable to an Arduino, and can in fact be programmed with the Arduino IDE.

The MiniBee has an accelerometer on board and you can connect other sensors through the pin header. There are expansion boards available that make it easy to hook up some sensors to the MiniBee.

The MiniBee needs an [XBee](#xbee) for the wireless communication.

# XBee {#xbee}

This is a board with a wireless chip made by the company [Digi](http://digi.com).

The XBee has a special configuration for use with the Sense/Stage MiniBee. When you buy a MiniBee, or a MiniBee Kit, the XBees are pre-programmed with the right settings to start using the Sense/Stage MiniBees right away, so that you do not need to figure out what settings to use. The settings of the XBees on the MiniBees are different from the settings of the XBee on the coordinator node.


# Firmware

The firmware is the code that runs on the MiniBee and takes care of the communication with the [XBee](#xbee), reading out the sensors and driving the actuators, based on the configuration that is received. When you buy a MiniBee, it comes preprogrammed with:

* the standard MiniBee firmware - which allows you to use the accelerometer and a lot of other sensors without having to program the MiniBee yourself
* a bootloader - which allows you to upload new firmware through the Arduino IDE, if you want to use customized firmware

The firmware is written in such a way that it communicates with the software that is provided for Sense/Stage.

# Coordinator node

The coordinator node is a board that connects the [XBee](#xbee) via USB to a computer. This is the bridge between the wireless communication between the XBees and the software running on the computer.

# Software

This software handles the communication via USB to the coordinator node, which in turn sends out messages to the XBees on the MiniBees, and receives messages from these.

The software is designed to interact with the firmware that runs on the MiniBees.

The software communicates with other programs using the OpenSoundControl (OSC) protocol.


# TODO

- links to other pages

