---
title: Customizing firmware
permalink: /sensestage-v1/customizing-firmware/
summary: Advanced guide explaining how to use the Arduino IDE to reprogram and customize the firmware on the Minibees. For example, to support special I2C sensors.

layout: guide
type: guide
guidestep: 0
featured-image:
level: advanced
priority: 5

creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: minibee
---

While the [default firmware supports a lot of common sensors and actuators](/sensestage-v1/basic-features-of-the-firmware) out of the box, in some cases you may need to customize the firmware to do something special. For example, you might have a specific I2C sensor, which requires that a certain library be included in the firmware. You may want to do some data manipulation on the board before sending it off into the network, or you might want to program some complex actuator behaviors on the board to be triggered by incoming network messages.

This guide will show you how you can customize the firmware to fit your needs.

## Summary

The MiniBee firmware is based on the Arduino framework, and the easiest way to adjust and upload new firmware code is to use the Arduino IDE. This guide assumes that you are already familiar with Arduino-based microcontroller programming to write your own customizations to the default firmware sketch.

If you want to send custom data __from__ the MiniBee out to the network, where "custom data" could be data from a special sensor, or data that has been manipulated in some way, you have to do the following:

- 1. [prepare the Arduino IDE for programming the MiniBee](/sensestage-v1/programming-the-minibee-with-arduino/)
- 2. Use the default firmware as a starting point for your new firmware, the default firmware is available in the [ssdn_minibee github repository](https://github.com/sensestage/ssdn_minibee)
- 3. Adjust the `setup()` function to include any setup code you need
- 4. Adjust the `loop()` function to include any code you need that will run on each loop
- 5. [Upload your customized firmware to your MiniBee](http://127.0.0.1:4000/sensestage-v1/programming-the-minibee-with-arduino/uploading-firmware)
- 6. Adapt the [configuration file](#adaptconfig) of your sensor network to include entries for your custom data

## Overview of the Default Firmware

The default firmware, along with important code libraries and Arduino IDE configuration files, can be found in the [ssdn_minibee github repository](https://github.com/sensestage/ssdn_minibee). You'll find the core Sense/Stage library in []/ssdn_minibee/libraries/MiniBee_APIn](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn) and a a number of useful examples of customized firmware inside the directory []/ssdn_minibee/libraries/MiniBee_APIn/examples](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn/examples).

A good starting sketch for customizing the firmware of [revision F MiniBees](/sensestage-v1/minibee-board-reference/) can be [found in the 'minibee_F' example](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn/examples/minibee_).

It should look something like this (comments added):


```
// needed for the ADXL library!
#include <Wire.h>

// this is the library for the on-board 3-axis accelerometer
#include <ADXL345.h>

// libraries for other popular sensors, you can safely comment these out
// if you would like to save space in the sketch
#include <LIS302DL.h>
#include <TMP102.h>
#include <BMP085.h>
#include <HMC5843.h>

// the core XBee library for radio communication
#include <XBee.h>

// the core Sense/Stage library that provides all MiniBee firmware functionality
#include <MiniBee_APIn.h>

// Create an instance of the MiniBee class
MiniBee_API mbee = MiniBee_API();

void setup() {
  // set up communication at 57600 baud (default) and board revision F
  mbee.setup( 57600, 'F' );
}

void loop() {
  // perform all the actions necessary to communicate sensor data each loop iteration
  mbee.loopStep();
}
```



## Custom firmware examples

 Inside the [examples directory](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn/examples) you'll find a number of custom firmwares that you can review to help with making your own custom firmware. These include:
------------------------

* Adding a Custom I2C Sensor (bno055)
* Smooth PWM control (ledfades)
* Timing-critical digital output (strobing a LED)
* Custom OSC messages
* Additional sensors
* Firmware with fixed configuration (configuration cannot be changed via Hive config file or OSC)
* Communicating from MiniBee to MiniBee
