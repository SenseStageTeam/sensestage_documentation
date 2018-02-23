---
title: Interfacing with MaxForLive
summary: This page describes how to interface with the MiniBees with Max For Live
layout: documentation
type: guide
creation-date: 2017-02-06
category: software
subcategory: examples
tags:
    - todo
---

# The files used in this guide, where to get them

# To include in the guide
    * screenshots
    * walk-through of what happens


# Assign a configuration via OSC

* receive `/minibee/info`
* receive `/minibee/status`
* send `/minibee/configuration`
* send `/minihive/configuration/save`

[Reference](assigning-a-minibee-configuration-via-osc)

# Receiving data

* receive `/minibee/data`
* route per minibee
* look at the values (numbers)
* look at the values (graphical)
* use the values in an example

# Sending data

* send PWM data to an LED w/ `/minibee/output`
* example of sending data (control the output rate!)

