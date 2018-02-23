---
title: LED blinking codes
summary: The four LEDs on the MiniBee give information about the status of the MiniBee. This page explains what each LED means.
layout: documentation
type: reference
creation-date: 2017-02-06
category: hardware
subcategory: minibee
tags:
    - todo
---


* When you turn the MiniBee on, a green LED will start burning; this is the middle one of the three LEDs next to the power switch. This indicates that power has turned on. If it is not burning when you switch power on, then there is a problem with the power supply (e.g. an empty battery).

* Right below the green LED there is an orange LED which will start blinking, once the XBee has woken up. This happens about 3 seconds after the MiniBee has turned on. If it doesn’t start blinking, either the XBee is missing, not configured correctly, or the battery power is too low to power the XBee

* Above the green LED there is a red LED, which will burn when the XBee is receiving data. It should burn when you start the swpydonhive script, as the configuration of the MiniBee is set up by the software. It should also burn whenever you send data to the MiniBee, e.g. if it is configured to have outputs and you are updating the data for the output.

* Above the GND/RX pins, below the XBees there is another green LED (connected to pin D4 of the microcontroller), which is used in the firmware and software to indicate the status of the MiniBee. If it stays on, there is a problem with updating the MiniBee’s configuration. In that case, turn the MiniBee on and off to restart the configuration process.

# TODO

- add pictures with the LEDs
