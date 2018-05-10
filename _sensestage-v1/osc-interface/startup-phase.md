---
title: Startup phase
summary: The messages that as a MiniBee is getting connected
layout: reference
type: reference
guidestep: 1
featured-image: 
parent: OSC interface

creation-date: 2017-02-06
category: software
subcategory: interfaces

tags:
    - osc
    - interface
    - communication

---

As a MiniBee gets connected to the communication software, the following messages are sent:

* an `info`-message detailing the serial number, the ID and the number of inputs and outputs of the MiniBee,
* a series of `status` messages that indicate in which phase of the startup the MiniBee is.

If no configuration is known for the MiniBee (there is none defined in the configuration file), an OSC message can be sent to [configure the MiniBee](assigning-a-minibee-configuration-via-osc).


```
    /minibee/info   - siii
```
*from MiniBee to user software*

Basic information on a MiniBee that has just connected to the hive. The arguments are:

* `s` - the serial number of the XBee that is on the MiniBee
* `i` - the id that is assigned to the MiniBee
* `i` - the number of inputs to the MiniBee - the number of sensor data values that it will send to the user software
* `i` - the number of outputs of the MiniBee - the number of actuator data values that can be sent to the hive


```
    /minibee/status - is
```
*from MiniBee to user software*

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

