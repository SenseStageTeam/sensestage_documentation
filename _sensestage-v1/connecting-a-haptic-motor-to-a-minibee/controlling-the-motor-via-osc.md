---
title: Controlling the motor via OSC
summary: A tutorial on how to connect a haptic vibration motor to a MiniBee and control it from your software.

layout: guide
guidestep: 4
parent: Connecting a haptic motor to a MiniBee

type: guide
level: basics
priority: 21

featured-image:
creation-date: 2018-02-06
category: introduction
subcategory: tutorials
related:
    - Configuration file
tags:
    - basics
    - actuators

status: fixmesoon
---

You can now send an OSC message from your software to control the motor:

- `/minibee/output 2 255` will turn the motor fully on.
- `/minibee/output 2 0` will turn the motor fully off.
- `/minibee/output 2 127` will turn the motor on at half strength.

The first argument is the ID of the MiniBee, the second argument the PWM value, which can be between 0 and 255.

If you connect multiple motors to one MiniBee, the messages will be:

- `/minibee/output 2 255 255` will turn both motors fully on.
- `/minibee/output 2 0 0` will turn both motors fully off.
- `/minibee/output 2 255 0` will turn the first motor fully on, and the second motor fully off

>>More information on the [OSC message format](../osc-message-reference/receiving-and-sending-data)