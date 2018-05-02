---
title: Selecting the Radio
summary: A guide on how to configure the XBee

layout: guide
type: guide
parent: Adding New MiniBees to a Network with XCTU
guidestep: 3


creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---

At this point you should have X-CTU installed, and have your coordinator board connected to your computer with the XBee you want to program seated into the board. If this isn't the case please go back and follow the earlier steps in this guide.

Now start up X-CTU. When you start the software you will see the following screen:

![](/img/x-ctu-startupscreen.png)

## Selecting the radio

The first thing you will need to do it have X-CTU detect the XBee device that you want to reprogram. Click on the `Add devices` button in the upper left corner to add a new device. You will get the following dialog:

![](/img/x-ctu-add-radio-module.png)

> Note: At this point you should already have your coordinator board connected to your computer with an XBee on top! If you plugged in your coordinator when the dialog is already open, click on the button `Refresh ports` to get an updated list of devices.


Now select the Serial/USB port corresponding to your coordinator board. On Linux, this should be something like `/dev/ttyUSB0`, on OSX something like `usbserial-AACC123`, on Windows something like `COM3`.

It may be that you need to change some settings in the lower half of the dialog. For example, if you are programming an XBee that came straight from the factory and was not purchased together with a Sense/Stage kit. If you are using a factory-fresh XBee, select `9600` for your baud rate. If the XBee has been used in a Sense/Stage setup before (or was bought with a Sense/Stage MiniBee), then select `57600` for the baud rate.

![](/img/x-ctu-choose-baudrate.png)

After selecting the USB port and checking the baudrate setting, click on the `Finish` button in the lower right corner. You will now get the following screen:

![](/img/x-ctu-discovering-radios.png)

In rare occasions, it cannot find the radio and asks you to reset the radio:

![](/img/x-ctu-action-required.png)

If this dialog shows up, push the button on the coordinator board that is at the edge under the XBee radio.

Once the radio has been found, you will see the following screen:

![](/img/x-ctu-select-radio-to-configure.png)

Click on the radio to see its current configuration. You will get a popup screen telling you that it is updating the user interface and reading the radio settings:

![](/img/x-ctu-reading-radio-settings.png)

After that, you will see a list of settings in the right half of the X-CTU window.


# Read settings of an XBee with X-CTU {#settings}

Once you have selected the radio to view its configuration, you will see the following screen:

![](/img/x-ctu-radio-settings.png)

The most important settings you may want to check are the Channel (CH) and pan id (ID), which specify the network that this radio will connect to. You may also want to check the power level (PL) - which determines the strength of the radio signal.
