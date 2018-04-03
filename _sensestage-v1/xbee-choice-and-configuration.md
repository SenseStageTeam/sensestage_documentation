---
title: XBee choice and configuration
summary: This page describes which XBee is used for Sense/Stage and which settings we are using in its configuration.
layout: documentation
type: guide
creation-date: 2017-02-06
tags: 
    - expert
category: hardware
subcategory: xbee
related:
  - Using X-CTU
---

The wireless transmission is done using the XBee wireless chip from [Digi](https://www.digi.com/). On this page we are explaining which one of the many available XBee chips we are using and what settings we are using for the one we have chosen.

## XBee variants

  * **transmission frequency**: The XBee chip is available in various flavours, either for the 900 MHz or 2.4 GHz range. We have only worked succesfully with the 2.4 GHz version. The 900 MHz ones have a different type of firmware with different settings.
  * **series**: The XBees that we have worked with successfully are the [**802.15.4 (or Series 1)**](https://www.digi.com/products/xbee-rf-solutions/2-4-ghz-modules/xbee-802-15-4); with **Series 2 (Zigbee/ZNET)** we encountered issues to both send data to a coordinator node and send data out to nodes (bidirectional transmission), which made it seem unusable for our system. We did however only test this in the AT-mode, not in the API-mode. But we chose to continue working only with the **Series 1**, so the Sense/Stage MiniBee system uses this version.
  * **range**: XBee and XBee Pro. The latter has a longer range than the regular XBee and can be useful for outdoor sensing. These two types can be mixed within one network. We ship the Sense/Stage MiniBees with the regular version, but you can exchange the XBee with an XBee Pro (from Series 1) provided you [configure it with our profile](using-x-ctu-to-configure-an-xbee).
  

## Configuration

The XBees can be configured with the [Digi software tool X-CTU](using-x-ctu-to-configure-an-xbee)).
  
The following settings are of interest to change:

  * **CH:** This is the channel or radio frequency the XBee will be transmitting on. All your XBees should have the same number here.
  * **ID:** This is the PAN ID, the identifier by which the XBees will know that they belong to the same network. All your XBees should have the same number here.
  * **DH and DL:** This is the address a node will send data to. In the Sense/Stage MiniBee system:
    - Coordinator node has as a basic **DH=0, DL=FFFA**. In fact, the coordinator will send targeted messages to individual MiniBees using the API mode an set target addresses for the messages.
    - The MiniBees use **DH=0, DL=0**. In fact, the MiniBee firmware will send targeted messages to the coordinator node using the API mode and set target addresses for the messages.
    - If you want to send data between the nodes themselves, you need to use another setting, but you can use the API for changing this on the fly.
    - The coordinator could also use **DH=0, DL=FFFF**, which broadcasts to all possible destinations.
  * **MY:** This is the address for the specific node. In the Sense/Stage MiniBee system:
    - The MiniBees have a default address of **MY=FFFA**. The address is automatically adjusted during the startup communication with the coordinator node and the hive software to set the address to the ID defined in the configuration file.
    - The coordinator node has a default address of **MY=0**.
    - If you want to send data between the nodes themselves, you can manually configure the MY addresses.
  * **CE:** This is the &#8220;Coordinator enable&#8221;. Should be 1 for the coordinator and 0 for the regular node.
  * **BD:** Setting for the baudrate. Should be the same for both coordinator node and regular node.
    - 57600 (BD 6) is used by the current version of the firmware (`MiniBee_APIn`) and the last AT-mode version (`MiniBee`).
    - 19200 (BD 4) was used by `MiniBeeV2`; library version 2.
  * **SM:** Sleep mode. This should be 2 (pin doze) for the regular node. For the coordinator node it depends whether or not the sleep pin (pin 2 of the XBee) is pulled low on the coordinator board. In case of doubt, set this to 0.
  * **API** The mode of the XBees for communication. The `MiniBee_APIn` firmware uses the API mode 2 (API 2). The API mode makes use of the firmware on the *XBee* to set target addresses and create packages of serial data to send out. It also does some checks to see whether a message arrived or not and sends the package again if it was not received. Our early versions (`MiniBeeV2` and `MiniBee`) of the firmware used the AT mode (API 0) - the transparent mode, which did not make use of these advanced features of the XBee firmware.

