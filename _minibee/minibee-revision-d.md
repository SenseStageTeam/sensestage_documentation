---
title: MiniBee Revision D
summary: The MiniBee revision D was the third version of the MiniBee, the production version. It was manufactured and sold between 2011 and 2016.
layout: documentation
type: reference
date: 2017-02-06
category: hardware
subcategory: minibee
related: 
    - Programming firmware with the arduino IDE
tags:
    - todo
---

![](/img/MiniBee_revD_XBee_header.jpg)


Overview of the board:

* 6 analog inputs: A0, A1, A2, A3, A6, A7
* 8 digital inputs or outputs: D3 and D5 to D11
* PWM (“analog”) output, at pins D3, D5, D6, D9, D10, D11
* I2C communication: SDA (A4), SCL (A5)
* Serial I/O: RX, TX (to XBee)
* Power input (between 3.3V and 5V), through battery connector and coin cell battery
* Regulated power output: 3.3V, GND
* green pcb

# Pins

The pin outs on the header are from left to right:

    GND - RX - D5 - D7 - D9 - D11 - A6 - SDA - A2 - A0
    3v3 - TX - D3 - D6 - D8 - D10 - A7 - SCL - A3 - A1

    
![](/img/minibee_annotated-D-front.jpg)
![](/img/minibee_annotated-D-back.jpg)

# LEDs


# Technical documents

* board layout
* schematic


[Design files for Eagle on github](https://github.com/sensestage/minibee_hardware/tree/master/minibee/revD)

# Changes to previous version

Revision D of the board has a few minor improvements on revision B:

* An additional LED on pin D4 for status indication.
* RX and TX also available on the output pin header.
* All bootloader programming pins broken out in the middle of the board


# Programming firmware and the bootloader

For [programming the firmware](programming-firmware-with-the-arduino-ide), use the board definition: "Sense/Stage MiniBee revB/D/F (3.3V, 12MHz) w/ Atmega328p"


# Subversions

The first manufacturing run has the Atmega328 chip instead of the Atmega328p chip. This is a subtle difference that only affects the board if you want to program the bootloader onto the board, or program firmware without using the bootloader. The boards of this first batch can be recognized by a sticker on the bottom with a serial number, and the desoldered pin holes. In the hardware definitions within the Arduino IDE, this version is called "Sense/Stage MiniBee revD0 (3.3V, 12MHz) w/ Atmega328". You *only* need this for programming the bootloader or programming the board with the Atmel programmer, not for the regular uploading of firmware.

![](/img/MiniBee_revD0.jpg)

![](/img/MiniBee_revD0_bottom.jpg)


# TODO

- check links