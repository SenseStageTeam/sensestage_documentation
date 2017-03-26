---
title: Prepare the Arduino IDE for use with Sense/Stage
summary: This page describes how to install the hardware and firmware files for the Arduino IDE
layout: documentation
type: guide
creation-date: 2017-02-06
tags: 
    - expert
category: firmware
subcategory: arduino-ide
---

To program the Sense/Stage MiniBee you have to use the Arduino IDE and prepare it to use the *firmware libraries* and the *hardware definitions* that we have created for Sense/Stage.

# Download files

* [Download the Arduino IDE](https://www.arduino.cc/en/Main/Software)

* [Download the Sense/Stage MiniBee files for Arduino](https://github.com/sensestage/ssdn_minibee)

# Install

* [Install the Arduino IDE](https://www.arduino.cc/en/Guide/HomePage)

## MiniBee files

* Unpack the `ssdn_minibee` package

* Check what your Arduino sketchbook folder is:
    * Go to `[FILE]` menu and choose `Preferences`, the keyboard shortcut is `[CTRL]`+`[,]`
    * At the top it tells you the folder for the `Sketchbook location`, e.g. `~/Arduino`
    * Go with your file browser to this folder
    * If there is no `hardware` folder there, just copy the folder `ssdn_minibee/hardware` to the sketchbook folder
    * If there is a `hardware` folder there, copy the folder `ssdn_minibee/minibee` to it
    * If there is no `libraries` folder there, just copy the folder `ssdn_minibee/libraries` to the sketchbook folder
    * If there is a `libraries` folder there, copy the folders in `ssdn_minibee/libraries` to it

* You should now have the following folders in your sketchbook folder:

```
hardware/
hardware/minibee
hardware/minibee/avr

libraries/ADXL345
libraries/BMP085
libraries/HMC58X3
libraries/LIS302DL
libraries/MBSerial
libraries/MiniBee
libraries/MiniBee_APIn
libraries/NewSoftSerial
libraries/OneWire
libraries/TMP102
libraries/XBee

```

> NOTE: the minibee files are for version 1.6.5 and up of the Arduino IDE. If you use an older version of the Arduino IDE, you have to use a [different branch of ssdn_minibee](https://github.com/sensestage/ssdn_minibee/tree/arduino_1-0)


The MiniBee Firmware examples will show up in the:

* **API-mode (recommended)** File -> Examples -> MiniBeeAPIn, and the MiniBee Firmware library will show up in Sketch -> Import Library… -> MiniBeeAPIn
* **AT-mode: (no longer maintained)** File -> Examples -> MiniBee, and the MiniBee Firmware library will show up in Sketch -> Import Library… -> MiniBee


# Firmware examples

* Now start the Arduino IDE
* In the `[FILE]` menu, under `Examples`, under `(Examples from Custom Libraries)` you have a set of examples for the `MiniBee_APIn` library.
* The example `minibee_F` is the default version for MiniBee revision F
* The example `minibee` is the default version for MiniBee revision D
* `customReceiving` shows how to receive custom data
* `customSending` shows how to send custom data
* `sendingPrivateData` shows how to send additional (private) messages
* `sendingTriggerData` shows how to send trigger data messages
* `BeeToBee` shows how to send data from one MiniBee to another
* `DS18x20_temperature` shows how to read out the DS18x10 temperature sensor
* `ITG3200` shows how to read out the ITG3200 sensor
* `LSM9DS1` shows how to read out the LSM9DS1 sensor
* `ledfades` shows how to set up a system with smoothly fading LEDs
* `minibeeServo` shows how to control a servo motor
* `minibeeNSS` shows how to use the NewSoftSerial library


# Choosing the board {#board}

* In the `[TOOLS]` menu, choose `[Sense Stage MiniBee]`
* The default processor is `ATmega328p revB/D/F (3.3V, 12 MHz)`
* Only for [revision A](minibee-revision-a#programmingfirmware) and [particular versions of revision D](minibee-revision-d#subversions) you need to choose a different processor.

