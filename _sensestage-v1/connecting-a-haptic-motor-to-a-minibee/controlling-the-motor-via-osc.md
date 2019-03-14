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

# Don't send messages too often

The MiniBee will only check for new messages every 25 ms (if you set the message interval to 25). So it does not make sense to send messages more often than that, or rather: if you send messages more often, you will overflood the MiniBee with messages and it will seem like the unit is not responding at all.
So if you use a fader or something similar to set the vibration level of the moter, then make sure that you only send out a message each 25 ms, and not each time the fader changes. A good approach is then the following: create a timer routine that checks every 25 ms whether the fader changed its value. If it changed, then send out an OSC message, if it did not change, don't send a message. This is illustrated in this flowchart:

![](/img/haptic/flowchart_osc.png)

If you want a smoother control over the vibration motor, then you will need to make custom firmware, where you can send messages to send a command to, for example: fade the intensity from 0 to 255 in one second and then fade out back to 0 in another second. So you would send a message describing a curve for the the motor to follow.

>>More information on [advanced control over outputs with custom firmware](../advanced-control-over-outputs-with-custom-firmware)

# Improving the reliability of the control messaging

As mentioned in the [previous page](the-configuration-file), you can adapt the message interval and the redundancy in the configuration file to improve the response of the MiniBee to control messages. Depending on how much other data (e.g. from the sensors) is being send through the Sense/Stage MiniBee system, you may need to adapt these values.

If this is not enough, then it may be worthwhile to use custom firmware for the MiniBee, so you can create a system in your software that will check whether a message was received, and resend it if it was not. This is also described in the tutorial about [advanced control over outputs with custom firmware](../advanced-control-over-outputs-with-custom-firmware).
