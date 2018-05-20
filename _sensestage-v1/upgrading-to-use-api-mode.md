---
title: Upgrading to use API mode
summary: How to upgrade your Xbees to use the more modern API mode. If you bought your Minibees in 2012 or later then this document is not relevant to you.
date: 2011-11-23T15:45:47+00:00
author: Marije Baalman

layout: documentation
type: guide
level: advanced
priority: 30

category: firmware
subcategory: minibee
---

> NOTE: THIS DOCUMENTS HOW TO UPGRADE TO USING THE API MODE FOR THE XBEES. IF YOU BOUGHT YOUR MINIBEES IN 2012 OR LATER, THIS DOCUMENT IS NOT RELEVANT FOR YOU_

To use the API mode for communication with the XBees you have to update the following things:

  * The settings of the XBees to use the API mode
  * The firmware on the MiniBee
  * Use the new version of the Hive software

## XBee settings

You can use the [X-CTU](using-x-ctu) to change the settings or simply load the [api profiles](https://github.com/sensestage/ssdn_xbee) onto your XBees. These are the profiles in the api subfolder.

Alternately, you can use the python [XBee Tools](using-command-line-xbee-tools) to change to the [API mode](using-command-line-xbee-tools/change-api-mode).

## MiniBee firmware

  * [Prepare the Arduino IDE with the right hardware files and firmware library](preparing-the-arduino-ide-for-use-with-sensestage)
  * Select the basic example from the Arduino menu: Examples>MiniBee_APIn>minibee
  * [And program it onto the MiniBee.](uploading-firmware-to-a-minibee)

## Use the new version of the Hive software

* [Install the software with these instructions](install-the-hive-software).


## Adjust your configuration files:

The libversion should now be 8:

`<minibee caps="7" configuration="1" id="1" libversion="8" name="minibee1" revision="D" serial="13A200407E506D">`

In the configuration file you can now use serial numbers with or withouth the leading zeros, so these two are equivalent:

`<minibee caps="7" configuration="1" id="1" libversion="8" name="minibee1" revision="D" serial="13A200407E506D">`

can also be:

`<minibee caps="7" configuration="1" id="1" libversion="8" name="minibee1" revision="D" serial="0013A200407E506D">`

![](/img/Xbee_serial.jpg)
