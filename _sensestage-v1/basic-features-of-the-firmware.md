---
title: Basic features of the firmware
summary: This page describes the basic functionality of the firmware
layout: documentation
type: guide
creation-date: 2017-02-06
tags: 
    - configuration
    - overview
category: firmware
subcategory: minibee
related:
    - Configuration file
    - Assigning a MiniBee Configuration via OSC
---


## Supported sensors and actuators

The MiniBee firmware library allows you to use most common sensors without having to reprogram the boards.

The sensor and actuation options supported by the library are:

  * Analog sensors (connected to the analog input pins, e.g. resistive sensors, analog accelerometers, infrared distance sensors)
  * Digital sensors (on/off, e.g. buttons and switches)
  * Accelerometer (on board ADXL345), a two wire interface (TWI or I2C) device.
  * PWM output (e.g. dimmable LEDs, motors)
  * Digital output (on/off)

## Configuration
    
Configuration is currently done through the XML configuration file (see [documentation on the hive client](configuration-file)) or [interactively via OSC](assigning-a-minibee-configuration-via-osc).

## What happens during the wireless configuration
    
* Board reads the serial number of the XBee and sends it to the coordinator
* Coordinator assigns an ID and tells the board whether or not it will receive a new configuration 
    * Board sends a message back that it is waiting
    * Coordinator sends configuration
* Board sends a summary of the current configuration (for the coordinator to verify)
* Board starts sending data



## Sensors supported in older firmware versions {#obsolete}

Up to firmware library version 8 the following additional two-wire sensors were supported:

* LIS302DL &#8211; accelerometer
* HMC58X3 &#8211; magnetometer
* TMP102 &#8211; temperature sensor
* BMP085 &#8211; barometric pressure and temperature

as well as

* SHT15: Relative humidity and temperature sensor
* Ultrasound sensors

In the newer versions the default support for these sensors has been removed, since new digital sensors are coming to the market fairly quickly, but also leaving the market faster than the MiniBee. So I've chosen to keep the MiniBee firmware small and add new digital sensors as examples of custom firmware rather than supporting them in the default firmware.
