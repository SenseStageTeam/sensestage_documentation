---
title: Charging LiPo Batteries
summary: How to charge LiIon batteries.

layout: guide
type: guide
parent: Guide to Batteries
guidestep: 1

creation-date: 2017-02-06
category: hardware
subcategory: battery
tags:
    - basics
status: backlist
---

To charge your LiPo batteries you'll need a special charger. We recommend [Sparkfun's LiPo charger basic](https://www.sparkfun.com/products/10401). Although many manufacturers make single-cell LiPo chargers that will also work fine, just make sure your charger has the same JST-PH 2mm connector as the Minibees do.

![](/img/battery/sparkfun-lipocharger-basic.jpg)
*Sparkfun's basic LiPo battery charger (USB cable not included!)*

1. unplug your battery from the MiniBee
2. connect the charger to a USB power source using an appropriate USB cable
3. connect your battery to the charger, the red LED will turn on while the battery is charging
4. once the LED turns __off__, your battery is charged

Each charger model works a little differently, so you should check the instructions for your specific brand.

The Sparkfun LiPo battery charger is especially nice because it can be embedded into your project, so that you can leave the battery attached to your MiniBee and only recharge it by connecting it to a USB power source. See the guide on [embedding the battery charger](/sensestage-v1/embedding-the-battery-charger/) for instructions on how to do this.

Otherwise, move on to the [next section](battery-strain-relief) to read about adding strain relief to your battery!
