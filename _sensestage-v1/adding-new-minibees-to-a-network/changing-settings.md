---
title: Changing settings
summary: A guide on how to configure the XBee

layout: guide
type: guide
parent: Adding New Minibees to a Network
guidestep: 4

creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---


Once you have selected the radio to view its configuration, you will see the following screen:

![](/img/x-ctu-radio-settings.png)

The settings you most likely want to change are the Channel, pan id and power level.

## Channel and pan id

The `channel` determines on which radio frequency the XBee are transmitting. In the 2.4 GHz band there are different subbands which can be used; which one to choose depends on what other frequencies are being used in the space, for example by WiFi routers. See [the documentation page on choosing a radio frequency](../choosing-a-radio-frequency-for-the-xbee) for a discussion about this.

The `pan id` is an identifier within the channel to distinguish different XBee networks from each other. XBees will just ignore traffic that is happening with different pan ids. `pan` is an acronym for 'Personal Area Network'.


In general, you just may want to change the channel and/or the pan id in order to have something different that the default setting the XBee is shipped with as part of the MiniBee set. This will avoid problems when you happen to be in the same space as someone else using the MiniBees. For example in your class with other students working with MiniBee sets, or in a concert or exhibition space.

## Power level

The international version of the XBee Pro has a higher power level than is generally allowed in Europe. So you will have to set the power level to 0 (the lowest) in order to be within European regulations for radio transmissions.

By default the power level is at 4.

## Changing the settings

You can click on the `i` on the left of a setting, to see a description of the setting. In the editing field on the right side, you can type the new value you want to use. There will be a popup, showing you the allowed values.

![](/img/x-ctu-adapt-setting.png)

Once you change the setting, the blue triangle will turn green, indicating that you changed the setting in the dialog, but have not written it to the radio yet.

![](/img/x-ctu-setting-changed.png)

## Writing the changed settings

You still need to write the settings to the XBee. For this, select `Write` from the menu, as shown in the screenshot.

![](/img/x-ctu-select-write-settings.png)

You may get a popup window that there are some empty values; don't worry about this and click ok.

![](/img/x-ctu-warning-empty-values.png)

You will get a popup window indicating that the settings are being written:

![](/img/x-ctu-writing-values.png)

After writing the values, the triangles that were green are now blue. This indicates that the values are written to the radio, but that they are different from the factory settings of the XBee.

![](/img/x-ctu-radio-settings.png)

You can now close the radio again by selecting the cross, see where the mouse cursor is in the screenshot:

![](/img/x-ctu-close-radio.png)

Now, disconnect the coordinator node from the computer and, if you want to configure another XBee, remove the XBee and place the new XBee on top. And [start again](selecting-the-radio).



# Old documentation (using the serial program)

* [Changing the Pan ID and channel of your Xbees](https://docs.sensestage.eu/old/changing-the-pan-id-and-channel-of-the-xbee)
* [Changing the transmission power (for XBee Pro)](https://docs.sensestage.eu/old/changing-the-power-level-of-the-xbee-pro)
