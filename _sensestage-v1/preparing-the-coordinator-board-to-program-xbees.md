---
title: Preparing the coordinator board to program XBees
summary: This page describes how to prepare the coordinator board to program XBees used with Sense/Stage.
layout: documentation
type: guide
creation-date: 2017-02-06
tags: 
    - todo
category: hardware
subcategory: xbee
---


Since the XBees for the MiniBees are programmed with sleep mode enabled, to reconfigure the XBees, you need to make a connection between the DTR and GND pin of the XBee on the coordinator node, otherwise the XBee will stay asleep and cannot be reconfigured.

The pictures below show (circled in red) which connections need to be made on the coordinator node. It is a very quick soldering effort!


{:.image-caption}
![](/img/coordinator_board_dtr_gnd_bottom.png)
![](/img/coordinator_board_dtr_gnd_top.png)
*Soldering the connection on the red Sparkfun coordinator board*

{:.image-caption}
![](/img/coordinator_board_dtr_gnd_dfrobot.png)
*Soldering the connection on the black DF Robot coordinator board*