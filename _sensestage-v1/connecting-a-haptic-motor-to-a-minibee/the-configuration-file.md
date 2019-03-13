---
title: The configuration file
summary: A tutorial on how to connect a haptic vibration motor to a MiniBee and control it from your software.

layout: guide
guidestep: 3
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

If you use the default firmware for the MiniBee, you can then define the pin you use to control the motor as an `AnalogOut`.

```
    <configuration id="4" message_interval="25" name="vibro" redundancy="3"
        samples_per_message="1">
      <pin config="AnalogOut" id="D3" name="haptic-motor"/>
    </configuration>
```

To improve the response of the control message you send, you can adapt:

- the `message_interval`: if you make it smaller, the firmware will more often check for new messages received.
- the `redundancy`: if you increase it, the hive software will send the message more often, thus improving the chance that the message is received.

You assign the configuration to a minibee, with aline like this:

```
     <minibee caps="7" configuration="4" id="2" libversion="10" name="" revision="F" serial="0013A200407E4F3B">
```

The important element is the `configuration="4"` pointing to the configuration with `id="4"`.

>>More information on the [configuration file format](../configuration-file)