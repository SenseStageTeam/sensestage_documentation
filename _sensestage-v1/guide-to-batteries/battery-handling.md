---
title: Safe Battery Handling
summary: What to consider when using a LiIon battery with a MiniBee.

layout: guide
type: guide
parent: Guide to Using LiPo Batteries
guidestep: 2

creation-date: 2017-02-06
category: hardware
subcategory: battery
tags:
    - basics
---


## Safety instructions for handling the LiIon batteries that are generally used with the Sense/Stage MiniBees:

* **Avoid piercing** of the batteries, if you package the battery close on the MiniBee, make sure that none of the pins of the MiniBee can pierce the battery. Add a protective coat around the battery with e.g. electrical tape or by placing a small plastic plate between the MiniBee board and the battery, so that it cannot be pierced.

* **Air travel:** Airline regulations state that loose LiIon batteries should be carried in **hand luggage**. I assume this has to do with changing air pressure and variable temperatures in the cargo part of the airplane, which can be a harmful environment for the batteries, and in the hand luggage, people will be able to see a possible fire and be able to take action. In any case, always make sure that you carry the batteries in your hand luggage when going on a plane and package them in a safe way: e.g in a small box where they cannot get crushed.

See also Sparkfun's [LiPo Battery tutorial](https://www.sparkfun.com/tutorials/241) for a lot of good advice and practical tips on:

- strain relief on the battery cable with electrical tape (so the wires won't break off after repeated use)
- how to use a wire cutter in a gentle way (not cutting the wire!) to unplug the battery from the JST connector


## Functional advice on placing the battery

* make sure that the battery does not cover the chip (or on-chip) antenna of the XBee on the MiniBee, otherwise the battery might actually block the wireless transmission.
