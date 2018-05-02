---
title: Preparing the coordinator board to program XBees
summary: This page describes how to prepare the coordinator board to program XBees used with Sense/Stage.

layout: guide
type: guide
parent: Adding New MiniBees to a Network with XCTU
guidestep: 2

creation-date: 2017-02-06
tags:
    - todo
category: hardware
subcategory: xbee
---

To program your XBee you'll need an [XBee programmer board](/sensestage-v1/coordinator-board). We recommend the [Sparkfun XBee Explorer USB](https://www.sparkfun.com/products/11812) because it has an on-board reset button that makes uploading new configurations much easier.

By default, XBees you purchase with the MiniBees are pre-programmed with sleep mode enabled. This means if you want to reconfigure the XBees on a programmer board without a reset button, you need to make a connection between the DTR and GND pin of the coordinator board to bring the XBee out of sleep mode. If the XBee stays asleep it cannot be reprogrammed.

The pictures below show (circled in red) which connections need to be made on the coordinator boards. It is a very quick soldering effort! _You only need to do this if you have a board without a reset button._


{:.image-caption}
![](/img/coordinator_board_dtr_gnd_bottom.png)
![](/img/coordinator_board_dtr_gnd_top.png)
*Soldering the connection on the red Sparkfun coordinator board without a reset button*

{:.image-caption}
![](/img/coordinator_board_dtr_gnd_dfrobot.png)
*Soldering the connection on the black DF Robot coordinator board*

Connect your coordinator board to your computer and connect the XBee you want to reprogram to the board.

_*NOTE*_ if this is your first time using the coordinator board you may need to go download the latest [FTDI virtual communication port drivers](http://www.ftdichip.com/Drivers/VCP.htm) before continuing.
