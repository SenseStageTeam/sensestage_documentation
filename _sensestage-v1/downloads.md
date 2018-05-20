---
title: Downloads
summary: Software Downloads
layout: documentation2
type: mainpage

creation-date: 2017-02-06
category: introduction
subcategory: glossary
tags:
    - todo
---

# Pydon

**Pydon** is the software at the core of Sense/Stage. In order to use Sense/Stage you'll need to first install this. Pydon translates data coming in from your sensor network into OpenSoundControl (OSC).

You can find [installation instructions for Pydon here](pydon-installation-guide)

All the files for Pydon can be found on our [github repository](https://github.com/sensestage/ssdn_python)

**OSX & Linux Download**
* [Zip file of the Pydon package from github](https://github.com/sensestage/ssdn_python/archive/master.zip)

**Windows Download**
* [Windows package](https://sensestage.eu/downloads/PydonWindowsPackage.zip)

# FTDI Virtual Com Port Drivers for Coordinator Node

Most coordinator nodes use a FTDI chip to translate the XBee serial data to USB. On OSX and Windows systems you need to install special Virtual Com Port drivers to be able to detect the coordinator board.

**OSX and Windows**
* [Download the VCP drivers directly from FTDI](http://www.ftdichip.com/Drivers/VCP.htm)

*NOTE: Windows users should download the 'setup executable' available through the link in the comments column.*

# Arduino firmware and hardware files

The firmware libraries and the hardware definitions that we have created for Sense/Stage for the Arduino IDE.

[Installation instructions can be found here](programming-the-minibee-with-arduino/prepare-the-arduino-ide)

* [Link to the github repository](https://github.com/sensestage/ssdn_minibee)

* [Directly download the zip file from github](https://github.com/sensestage/ssdn_minibee/archive/master.zip)

# XBee profiles

When using new XBees in your Sense/Stage network, you will need to upload special profiles to them using XCTU. This repository contains those profiles.

[Profile installation instructions](adding-new-minibees-to-a-network-with-xctu/)

* [Link to the github repository](https://github.com/sensestage/ssdn_xbee)

* [Directly download the zip file from github](https://github.com/sensestage/ssdn_xbee/archive/master.zip)


# Hardware design files

The hardware design files for the MiniBees; in Eagle (up to revision D) and KiCad (from revision F and up).

[Overview of all the minibee boards](minibee-board-reference/)

* [Link to the github repository](https://github.com/sensestage/minibee_hardware)
* [Directly download the zip file from github](https://github.com/sensestage/minibee_hardware/archive/master.zip)
* [Overview of the expansion boards](expansion-boards/)
