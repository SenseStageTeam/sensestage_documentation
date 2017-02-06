---
title: MiniBee Revision F
summary: The MiniBee revision F is the fourth version of the MiniBee, the second production version. It is manufactured and sold from 2017.
layout: documentation
type: reference
date: 2017-02-06
category: hardware
subcategory: minibee
---

The MiniBee revision F is the fourth version of the MiniBee, the second production version. It is manufactured and sold from 2017.


Overview of the board:

* 6 analog inputs: A0, A1, A2, A3, A6, A7
* 8 digital inputs or outputs: D3 and D5 to D11
* PWM (“analog”) output, at pins D3, D5, D6, D9, D10, D11
* I2C communication: SDA (A4), SCL (A5)
* Serial I/O: RX, TX (to XBee)
* Power input (between 3.3V and 16V), through battery connector and coin cell battery
* Regulated power output: 3.3V, GND
* blue pcb

# Pin out

The pin outs on the header are from left to right:

    GND - RX - D5 - D2 - D9 - D11 - A6 - SDA - A2 - A0
    3v3 - TX - D3 - D6 - D8 - D10 - A7 - SCL - A3 - A1


# LEDs


# Technical documents

* board layout
* schematic

[Design files for KiCad on github](https://github.com/sensestage/minibee_hardware/tree/master/minibee/revF)

# Changes to previous version

Revision F of the board has a few improvements on revision D based on the feedback from users:

* a blue pcb to distinguish it easily from previous revisions
* a different on/off switch, which is both mechanically and electronically more sturdy
* a 300 mA voltage regulator instead of 150 mA
* pads on the bottom that break out power supply, the on/off switch, and the interrupt pins of the accelerometer
* an exchange of pin D2 and D7 - so that the interrupt capability of D2 can be used by the user (a firmware update is forthcoming)

Also the design has been moved from the (closed source) Eagle software to the open source [Kicad](http://kicad-pcb.org/) software, so that the design of this open source hardware module is now also made with open source software.


# Programming firmware and the bootloader

For [programming the firmware]({{base_url}}/minibee/programming-firmware-with-the-arduino-ide), use the board definition: "Sense/Stage MiniBee revB/D (3.3V, 12MHz) w/ Atmega328p"

