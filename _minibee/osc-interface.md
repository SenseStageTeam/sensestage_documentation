---
title: OSC interface
summary: This page describes the OSC messages that the Sense/Stage software sends and understands
layout: documentation
type: reference
date: 2017-02-06
category: software
subcategory: interfaces
tags:
    - todo
---

# How to read this description

OSC messages consist of an OSC-address (something like `/hello/osc/address`) and a number of data arguments that can be of different types, like integers (`i`), floating point values (`f`) or strings (`s`). In this description of the OSC interface of the Sense/Stage software we list the OSC address that is used, followed by the argument types of the data values that are sent or expected with it. If there is a `..` in the argument list, then there is a variable number of data values of the preceding type. Optional arguments are indicated in brackets, e.g. `(s)`.

# Basic usage

## OSC commands from the hive to the user software

```
    /minibee/info   - siii
```

Basic information on a MiniBee that has just connected to the hive. The arguments are:

* `s` - the serial number of the XBee that is on the MiniBee
* `i` - the id that is assigned to the MiniBee
* `i` - the number of inputs to the MiniBee - the number of sensor data values that it will send to the user software
* `i` - the number of outputs of the MiniBee - the number of actuator data values that can be sent to the hive


```
    /minibee/status - is
```

Status information of the MiniBee.

* `i` - the ID of the MiniBee
* `s` - the status of the minibee, which can be one of:
    - `init` - the status as the software starts up
    - `waiting` - waiting to be configured
    - `configured` - the minibee is configured with its sensor/actuator configuration
    - `receiving` - data is being received from the minibee
    - `active` - the minibee is active, but its configuration is such that it does not send sensor data
    - `off` - the minibee is off, this status message is sent out after no data has been received for a while from the minibee
    - `paused` - the minibee has been paused

```
    /minibee/data   - iff..f
```
    
* `i` - the ID of the MiniBee
* `ff..f` - a number of floating point data values that correspond to the sensors that are attached. The order of these values is always:
    - data values sent from customized firmware
    - digital pin values
    - analog pin values
    - I2C device values (those supported by the standard firmware), typically these are the three accelerometer values
    - received signal strength (RSSI), if enabled in the configuration

## OSC commands from the user software to the hive

```
    /minibee/output - iii..i
```

* `i` - the ID of the MiniBee
* `ii..i` - as many integer data values that the MiniBee has as outputs (the number of values you send has to match exactly the number of outputs that are defined for the MiniBee). The order is:
    - PWM values (in the range of 0 to 255) in the order of pin number (so D3, D5, D6, D9, D10, D11)
    - digital values (0 or 1) in the order of pin number


# Advanced usage

## Configuration

You can configure a MiniBee by sending a message to the hive with the configuration ID that you want the MiniBee to have:

    /minibee/configuration - ii(s)

* `i` - the ID of the MiniBee
* `i` - the ID of the configuration; this configuration has to be defined in the configuration file
* `s` - (optional) the serial number of the MiniBee

The hive sends a message back to confirm or to indicate an error. The arguments are the same as the message above.

    /minibee/configuration/done  - ii(s)
    /minibee/configuration/error - ii(s)


You can load and save a configuration file via OSC:

    /minihive/configuration/save  - s 

* `s` - the filename to save to

    /minihive/configuration/load  - s 

* `s` - the filename to load from

## Controlling the behaviour of the MiniBee

There are some advanced options to control what a MiniBee is doing.

*Pausing a minibee:*

    /minibee/run - ii
    
* `i` - the minibee id
* `i` - whether to pause (0) or run (1) the minibee

Getting a *loopback* message sent back from the minibee, i.e. a copy of each message sent to the minibee. This is useful for debugging.

    /minibee/loopback - ii

* `i` - the minibee id
* `i` - 0 (for not sending messages back) or 1 (for sending each message back)

*Re-initialize the MiniBee firmware*

If you want to re-initialize the firmware (without resetting it), you can send a message to do so. This can be useful if a MiniBee was already on, when you started the software. 

    /minibee/announce - i

* `i` - the minibee id

*Reset a MiniBee.*

This will reset the Atmega328 chip, so effectively restart the firmware. This can be useful if for some reason the MiniBee got stuck.

    /minibee/reset - i

* `i` - the minibee id

To reset all minibees:

    /minihive/reset

*Save the ID of the XBee*. By default the XBees have an ID of 0xFFFA. During the configuration process the ID is set to the number defined in the configuration file. If you want to save this ID to the MiniBee, this step will not be necessary in the configuration process, and the startup procedure may go a little bit faster.

    /minibee/saveid - i

* `i` - the minibee id

To save the IDs on all minibees that are turned on:

    /minihive/ids/save


# Custom messages

## OSC commands from the hive to the user software

```
    /minibee/private   - iff..f
```

* `i` - the ID of the MiniBee
* `ff..f` - a number of floating point data values that correspond to the sensors that are attached. The order of these values is always:

```
    /minibee/trigger   - iff..f
````

* `i` - the ID of the MiniBee
* `ff..f` - a number of floating point data values that correspond to the sensors that are attached. The order of these values is always:


## OSC commands from the user software to the hive

```
    /minibee/custom - iii..i
```

* `i` - the ID of the MiniBee
* `ii..i` - as many integer values as you have defined in your custom firmware. You have to make sure in your user software that the integer values that you send are in the range of 0 to 255.


# On the fly configuration via OSC


--- set configuration ---
/minihive/configuration/create

Format:
i config id
s config name
i samples per message
i message interval
i number of pins defined (N)
i number of TWI devices defined (M)

then N times:
  s      - pin id (e.g. A0)
  s or i - pin function (e.g. 3, or 'AnalogIn')
  s      - pin label (e.g. light)

then M times:
  i      - twi id (e.g. 0)
  s or i - twi function (e.g. 10, or 'ADXL345')
  s      - twi label (e.g. accelero)

/minihive/configuration/short (as above but without separate pin definitions; those are done separately by the message that follow)
/minihive/configuration/pin config id, pinid, pinconfig
/minihive/configuration/twi config id, twiid, twiconfig

--- query configuration ---
/minihive/configuration/query config id

/minihive/configuration/pin/query config id, pinid
/minihive/configuration/twi/query config id, twiid



--- delete a configuration
/minihive/configuration/delete config id

  possible return messages:
    /minihive/configuration/error config id
    /minihive/configuration/delete/done config id

# TODO

- configuration section
