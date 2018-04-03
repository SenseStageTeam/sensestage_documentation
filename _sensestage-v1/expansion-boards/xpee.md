---
title: XPee
summary: The XPee board is a small expansion board that allows you to easily hook up 4 resistive sensors and 3 LEDs.
type: reference
parent: expansion-boards
layout: reference
guidestep: 2
creation-date: 2017-02-06
category: hardware
subcategory: expansion
tags:
    - todo
---


The XPee board is a small expansion board which allows you to hook up common sensors:

* 4 resistive sensors
* 3 LEDs
* 3 digital inputs or outputs
* Two wire interface (TWI/I2C) devices
* RX/TX (for monitoring)

For the resistive sensors footprints on the board are available to solder a (fixed value) resistor to create the voltage divider with your resistive sensor.

For the LEDs there are also footprints available to solder the (fixed value) resistor to regulate the current to your LED.

![](/img/XPee.png)

# Technical documents

![](/img/xpee_schematic.png)

[Design files for KiCad on github]()

# Examples

{:.image-caption}
![](/img/xpee_example_ldr_led.jpg)
*An example of an XPee with an LDR connected to A0 and an LED to D9*

# TODO

- update github link