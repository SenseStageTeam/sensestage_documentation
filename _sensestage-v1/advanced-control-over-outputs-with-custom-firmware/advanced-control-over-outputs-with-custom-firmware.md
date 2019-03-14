---
title: Advanced control over outputs with custom firmware
summary: A guide for creating more detailed control over outputs using custom firmware

permalink: /sensestage-v1/advanced-control-over-outputs-with-custom-firmware/

layout: guide
guidestep: 0

type: guide
level: advanced
priority: 9

featured-image:
creation-date: 2018-02-06
category: introduction
subcategory: tutorials
related:
    - Customizing firmware
    - Programming the MiniBee with Arduino
tags:
    - advanced
    - actuators

status: fixmesoon
---

In some cases you want to have more detailed control over the PWM outputs of a MiniBee. For example when you use [haptic motors](connecting-a-haptic-motor-to-a-minibee) or when you control LEDs with a MiniBee.

The main reaons for doing this are:

- Implement a mechanism to confirm that a control message was received by the MiniBee. If a message was not received, then your software can resend the message.
- To create smoother curves for fading in and out an LED, or the intensity of the haptic vibration. Or you might even define patterns for blinking (e.g. three short blinks; one short, one long, one short blink) or vibration.

# Preparation

To do this, you will need to program custom firmware for the MiniBee.

The guide ["Programming the MiniBee with Arduino"](../programming-the-minibee-with-arduino) will explain how to prepare the coordinator board for programming the MiniBee, how to prepare the Arduino IDE and how the uploading of the firmware you will write will work.

The guide ["Customizing firmware"](customizing-firmware) is a general guide on how to customize the firmware and can help you to understand the available options in the MiniBee firmware library for customization.
