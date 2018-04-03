---
title: Customizing firmware
permalink: /sensestage-v1/customizing-firmware/index.html
summary: This page describes how to write custom firmware
layout: guide
type: guide
guidestep: 0
featured-image: feature-thumb2.jpg
creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: minibee
---

While the [default firmware supports a lot of common sensors and actuators](basic-features-of-the-firmware), in some cases you may want to customize the firmware to do something specific, e.g. when you have a sensor that is not covered by the default firmware, or when you want to perform some data parsing on the board. This guide will show you how you can customize the firmware to your needs.

## General approach

The firmware based on Arduino. To customize the firmware you have to:

If you want to send custom data from the MiniBee, you have to:

- [prepare the Arduino IDE](prepare-the-arduino-ide-for-use-with-sense-stage)
- adjust the `setup()` function
- adjust the `loop()` function
- [upload the customized firmware to your MiniBee](uploading-firmware-to-a-minibee)
- adapt the [configuration file](#adaptconfig)

## The starting point

The default firmware looks like this (see the [`MiniBee_F` example](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn/examples/minibee_F)):

```
// needed for ADXL:
#include <Wire.h>

#include <ADXL345.h>

// needed for communication:
#include <XBee.h>

// our library:
#include <MiniBee_APIn.h>

// instantiate a minibee:
MiniBee_API Bee = MiniBee_API();

void setup() {
  // setup at baudrate 57600 (default) for board revision 'F'
  Bee.setup( 57600, 'F' );
}

void loop() {
  // perform all the actions that need to be taken in a loop step:
  Bee.loopStep();
}
```






[Custom firmware examples](https://docs.sensestage.eu/customizing-the-minibee-firmware)
------------------------

* Custom I2C Sensor
* Impossible SPI communication (not really possible; SPI pins are not broken out)
* Smooth PWM control
* Timing-critical digital output (strobing a LED)
* Custom OSC messages
* Additional sensors


* Firmware with fixed configuration (configuration cannot be changed via Hive config file or OSC)
* Communicating from MiniBee to MiniBee
