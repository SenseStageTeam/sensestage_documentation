---
title: Guide to Batteries
summary: An overview of the kinds of batteries that can be used with your sensor nodes, including how to charge and care for the most popular battery type, Lithium Polymer (LiPo) batteries. Importantly, this guide includes safety advice for using LiPo batteries in your projects.

layout: guide
type: guide
guidestep: 0
featured-image:
level: basics
priority: 7

creation-date: 2018-03-28
category: hardware
subcategory: battery
tags:
    - overview
status: complete

permalink: /sensestage-v1/guide-to-batteries/
---

What kind of battery to use to power your sensor nodes (MiniBees)?

Lithium Ion Polymer batteries, also known as LiPo and Li-Poly batteries, are the battery type we recommend. Most commonly used in mobile phones, these batteries are flat, rechargeable, and pack a lot of energy into a small package. We recommend using the single-cell variety.

Each Minibee includes a standard JST-PH 2-pin male connector for attaching a battery. [The female equivalent of this connector can be found at Adafruit](https://www.adafruit.com/product/261), amongst other vendors). LiPo batteries come in many varieties, so when choosing one you should make sure that it has the JST-PH 2-pin 2mm pin spacing connector.


![](/img/battery/minibee-lipo-connect-04.jpg)
*Minibee with a 400mAh LiPo battery attached (the XBee is removed so you can see the connector)*


Both [Sparkfun](https://www.sparkfun.com/categories/54) and [Adafruit](https://www.adafruit.com/category/574) (and their distributors) carry batteries with the appropriate connectors.

## Note! Be careful when removing the battery!

The connectors on these LiPo batteries are not really designed to be disconnected and reconnected repeatedly, but that's likely what you'll be doing when you're building your wireless sensing projects. Because of this, you should be especially careful when removing the battery from a MiniBee. __NEVER__ pull out the battery by the cable, __ALWAYS__ pull it out by the connector. It can help to use a pair of pliers or flush cutters (held gently) to disconnect the battery.

![](/img/battery/minibee-battery-removal.gif)
*Gently wiggling out the battery by the connector with a pair of flush cutters*

For more tips on adding strain relief to your battery, see the step on [strain relief](battery-strain-relief) in this guide.

## How much capacity do you need?

The capacity of LiPo batteries is usually measured in milliamp-hours. This is the number of milliamps of current the battery should be capable of delivering consistently for one hour. So, if you had a battery that was rated 400mAh, and you have it connected to a circuit that draws 400mA of current, then you can expect the battery to last for 1 hour.

When purchasing a LiPo battery, it's good to consider the needs of your project. There is always a compromise to be made between battery size and battery capacity.

The Minibee board draws about 70 mA of current when used with a regular XBee, transmitting data every 50 ms. So, assuming you have a 400mAh LiPo battery, you could expect roughly 5.7 hours (400 divided by 70) of operation on a single charge with this battery. Although, depending on what sensors you have attached, you may consume more current.
