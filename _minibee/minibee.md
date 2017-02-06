---
title: MiniBee
subtitle: different versions of the MiniBee hardware
summary: There are several versions of the MiniBee. This page describes the main features of the MiniBee and links to the different versions of the board.
layout: documentation
type: overview
date: 2017-02-06
category: hardware
subcategory: minibee
---

The Sense/Stage MiniBee is a small microcontroller board based on the Arduino, integrated with a connection for an XBee wireless chip. It is small and comes with preloaded firmware to use it easily in your wireless projects for a lot of common sensing and actuating purposes. As a bonus there is a 3-axis accelerometer on board. Cross platform open source software sends the data from the boards to your interactive environment via OpenSoundControl (OSC).

![]({{ base_url }}/img/minibee_bare.jpg)

Overview of the features:

* 6 analog inputs: A0, A1, A2, A3, A6, A7
* 8 digital inputs or outputs: D3, D5, D6, D7, D8, D9, D10, D11; or optional four more: A0, A1, A2, A3
* PWM (“analog”) output, at pins D3, D5, D6, D9, D10, D11
* TWI (or I2C) communication: SDA (A4), SCL (A5)
* Integrated ADXL345 – 3-axis accelerometer
* Serial I/O: RX, TX (to XBee)
* Power input (between 3.3V and 5V), through battery connector and coin cell battery
* Regulated power output: 3.3V, GND
* On/off switch
* Short circuit protection with a resetting fuse
* Status LEDs for power, association with XBee network, XBee receiving data, and configuration status
* Small footprint
* Preprogrammed with firmware for wireless configuration for using many common sensors
* Firmware communication with software data sharing network supported by many common interactive software environments (e.g. SuperCollider, Max/MSP, PureData, Processing).
