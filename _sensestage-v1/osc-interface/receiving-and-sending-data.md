---
title: Receiving and sending data
summary: 
layout: reference
type: reference
guidestep: 2
featured-image: 
parent: OSC interface

creation-date: 2017-02-06
category: software
subcategory: interfaces

tags:
    - osc
    - interface
    - communication

status: complete
---

The data from the sensors of the MiniBee is sent with a message `/minibee/data`. The received signal strength with a message `/minibee/rssi`.

You can send data to the output pins of the MiniBee with the message `/minibee/output`.



```
    /minibee/data   - iff..f
```
*from MiniBee to user software*
   
* `i` - the ID of the MiniBee
* `ff..f` - a number of floating point data values that correspond to the sensors that are attached. The order of these values is always:
    - data values sent from customized firmware
    - digital pin values
    - analog pin values
    - I2C device values (those supported by the standard firmware), typically these are the three accelerometer values
    - received signal strength (RSSI), if enabled in the configuration (in pydon version below v0.42)

```
    /minibee/rssi   - if
```
*from MiniBee to user software*

* `i` - the ID of the MiniBee
* `i` - a number of integer data value that corresponds to the received signal strength (RSSI)
    
> only available in pydon version 0.42 and up.




```
    /minibee/output - iii..i
```
*from user software to MiniBee*

* `i` - the ID of the MiniBee
* `ii..i` - as many integer data values that the MiniBee has as outputs (the number of values you send has to match exactly the number of outputs that are defined for the MiniBee). The order is:
    - PWM values (in the range of 0 to 255) in the order of pin number (so D3, D5, D6, D9, D10, D11)
    - digital values (0 or 1) in the order of pin number

