---
title: Programming the MiniBee with Arduino
permalink: /sensestage-v1/programming-the-minibee-with-arduino/
summary: A guide on how to program firmware onto the MiniBee with the Arduino IDE
layout: guide
type: guide
guidestep: 0
creation-date: 2017-02-06
level: advanced
priority: 8
featured-image:
tags:
    - expert
    - todo
category: firmware
subcategory: arduino-ide
---

In this guide we will explain how you can use the Arduino IDE to program the MiniBees.

The MiniBee itself is a small form-factor Arduino board running at a clock speed of 12Mhz. When you buy a MiniBee, it is preprogrammed with the bootloader and the default MiniBee firmware sketch. The Sense/Stage system is designed so that you should rarely, if ever, need to reprogram your MiniBees, because all configuration is done via the [XML configuration file in Pydon](/sensestage-v1/configuration-file/configuration-file), or through [OSC messages](/sensestage-v1/creating-minibee-configurations-via-osc/).

You will only need to program firmware yourself in case you need to update the firmware to a newer version, or when you need to modify the firmware to support specific sensors or do on-board data manipulations. For more information see the [advanced guide on customizing firmware](/sensestage-v1/customizing-firmware).

## Summary

* [Make a connection between the MiniBee and the coordinator board](connecting-the-minibee-and-coordinator-board)
* [Prepare the Arduino IDE with firmware libraries and hardware definitions](prepare-the-arduino-ide)
* [Uploading firmware to a MiniBee](uploading-firmware)
* [Programming the bootloader](programming-the-bootloader) - in case you happen to have a MiniBee with no bootloader
