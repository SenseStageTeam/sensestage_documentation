---
title: MiniBee Revision D
summary: The MiniBee revision D was the third version of the MiniBee, the production version. It was manufactured and sold between 2011 and 2016.
type: reference
parent: minibee-types
layout: reference
guidestep: 3
creation-date: 2017-02-06
category: hardware
subcategory: minibee
related: 
    - Programming firmware with the arduino IDE
    - Prepare the Arduino IDE for use with Sense/Stage
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

There are four LEDs on the MiniBee revision D:

* a red LED to indicate that the MiniBee is receiving data from the coordinator node. This one only goes on for about a second, when the XBee is receiving data.
* a green LED to indicate that the MiniBee is on. This one will be on if you have switched the power on.
* an orange LED to indicate that the XBee is associating with a network and that it is on. This one will be blinking.

{:.image-caption}
![](/img/minibee-rev-d-leds-top.png){:width="200px"}
*LEDs for receiving data, power, association (xbee on)*

{:.image-caption}
![](/img/minibee-rev-d-led-labels.png){:width="200px"}
*labels on the back for receiving data, power, association (xbee on)*


* a green LED is just between the XBee header and the extension header. This one is used inside the firmware to indicate that the module is sending out data.

{:.image-caption}
![](/img/minibee-rev-d-leds-status.png){:width="200px"}
*status LED near the header*

# Technical documents


Board layout and schematic are available here: [design files for Eagle on github](https://github.com/sensestage/minibee_hardware/tree/master/minibee/revD)

# Changes to previous version

Revision D of the board has a few minor improvements on revision B:

* An additional LED on pin D4 for status indication.
* RX and TX also available on the output pin header.
* All bootloader programming pins broken out in the middle of the board


# Programming firmware and the bootloader

For [programming the firmware](prepare-the-arduino-ide-for-use-with-sense-stage#board), use the board definition: `Sense/Stage MiniBee revB/D/F (3.3V, 12MHz) w/ Atmega328p`


In the source code of customized firmware, make sure that you use revision D, so the `Bee.setup` command should be:

```
Bee.setup(57600,'D');
```


# Subversions {#subversions}

The first manufacturing run has the Atmega328 chip instead of the Atmega328p chip. This is a subtle difference that only affects the board if you want to program the bootloader onto the board, or program firmware without using the bootloader. The boards of this first batch can be recognized by a sticker on the bottom with a serial number, and the desoldered pin holes. In the hardware definitions within the Arduino IDE, this version is called `Sense/Stage MiniBee revD0 (3.3V, 12MHz) w/ Atmega328`. You *only* need this for programming the bootloader or programming the board with the Atmel programmer, not for the regular uploading of firmware.

![](/img/MiniBee_revD0.jpg)

![](/img/MiniBee_revD0_bottom.jpg)


You may also need [this section](/download/atmega328_avrdude.conf) in the `avrdude.conf` file that is in the `hardware/tools/` folder of your copy of Arduino if you want to program with an AVR programmer onto the chip (e.g. for changing the bootloader, or bypassing it):
