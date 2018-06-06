---
title: Safe Battery Handling
summary: What to consider when using a LiIon battery with a MiniBee.

layout: guide
type: guide
parent: Guide to Batteries
guidestep: 3

creation-date: 2017-02-06
category: hardware
subcategory: battery
tags:
    - basics
---


## Safety instructions for handling LiPo batteries

LiPo batteries are potentially fire hazards and you should take caution when using them. Be especially aware that most air travel regulations forbid putting LiPo batteries in checked luggage. You can only bring them in your carry-on luggage.

## Avoid Piercing the batteries.

Pins and other sharp edges can potentially puncture the wrapping of the LiPo battery and start a fire. This is especially good to keep in mind if you package the battery against the MiniBee, where the soldered pins on the bottom of the board could potentially puncture the batter. Make sure that none of the pins of the MiniBee can pierce the battery. Add a protective coat around the battery with e.g. electrical tape or by placing a small plastic plate between the MiniBee board and the battery, so that it cannot be pierced.

![](/img/battery/minibee-battery-sandwich-03.jpg)
*A MiniBee-Battery sandwich with some electrical tape in between to protect the battery from being punctured*

## Air travel
Airline regulations state that loose LiIon batteries should be carried in **hand luggage**. I assume this has to do with changing air pressure and variable temperatures in the cargo part of the airplane, which can be a harmful environment for the batteries, and in the hand luggage, people will be able to see a possible fire and be able to take action. In any case, always make sure that you carry the batteries in your hand luggage when going on a plane and package them in a safe way: e.g in a small box where they cannot get crushed.

See also Sparkfun's [LiPo Battery tutorial](https://www.sparkfun.com/tutorials/241) for a lot of good advice and practical tips.

## Finally, some Functional advice on placing the battery

* Make sure that the battery does not cover the chip (or on-chip) antenna of the XBee on the MiniBee, otherwise the battery might actually block the wireless transmission.

![](/img/battery/onboard-antenna.png)
