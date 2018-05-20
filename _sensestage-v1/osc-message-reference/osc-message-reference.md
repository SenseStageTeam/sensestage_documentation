---
title: OSC Message Reference
summary: An overview of OSC messages that are sent and received in Sense/Stage.
layout: reference
type: reference
guidestep: 0
featured-image:

permalink: sensestage-v1/osc-message-reference

creation-date: 2017-02-06
category: software
subcategory: interfaces

tags:
    - osc
    - interface
    - communication

status: complete
---

# How to read this reference

The Pydon software

OSC messages consist of an OSC-address (something like `/hello/osc/address`) and a number of data arguments that can be of different types, like integers (`i`), floating point values (`f`) or strings (`s`). In this description of the OSC interface of the Sense/Stage software we list the OSC address that is used, followed by the argument types of the data values that are sent or expected with it. If there is a `..` in the argument list, then there is a variable number of data values of the preceding type. Optional arguments are indicated in brackets, e.g. `(s)`.
