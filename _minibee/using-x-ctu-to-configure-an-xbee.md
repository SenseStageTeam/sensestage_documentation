---
title: Using X-CTU to configure an XBee
summary: This page describes how to use X-CTU to load an XBee configuration profile onto an XBee, to prepare the XBee for use with the Sense/Stage MiniBee.
layout: documentation
type: guide
creation-date: 2017-05-04
tags: 
category: hardware
subcategory: xbee
related:
  - Using X-CTU to change settings of an XBee
---

# Getting X-CTU {#getting}

X-CTU is free software from [Digi](https://www.digi.com) that allows you to configure the XBees. The software is written in Java and is crossplatform, so it can be used on Windows, OSX and Linux.

Use [this direct link](https://www.digi.com/products/xbee-rf-solutions/xctu-software/xctu) to get to the X-CTU page. In case the direct link does not work, search on the [website of Digi](httsp://www.digi.com) for the software in the search field with the keyword `X-CTU`.

Click on the *Download* link on the website to get the software.


# Getting the XBee profiles for the Sense/Stage MiniBee {#profiles}

The XBee profiles for Sense/Stage are available from [](https://github.com/sensestage/ssdn_xbee). Click on the `Clone or Download` button, or use this [direct link for a zip-file](https://github.com/sensestage/ssdn_xbee/archive/master.zip).

Unpack the folder. The layout of the folders is as follows:

* In the folder `at`, the files are for the old AT mode, which were used with older (before 2012) MiniBee firmware.
* In the folder `api`, the files are for the API mode. These are the ones that are used with the current MiniBee firmware.
* The folder `api` is further subdivided in `pro` with profiles for the XBee Pro, and `regular` for the normal XBees.
* In the folder `regular` you find 6 files; the ones with `coordinator` in are used for the coordinator board, the ones with `enddevice` in the name are used for the XBees on the MiniBees.
    - `wscoordinator_api.pro` - version for old X-CTU software
    - `wsenddevice_api.pro` - version for old X-CTU software
    - `coordinator_1155_api2.xml` - version for new X-CTU software
    - `enddevice_1155_api2.xml` - version for new X-CTU software
    - `coordinator_2017F_10ef.xml` - current version with which MiniBee revision F is shipped
    - `enddevice_2017F_10ef.xml` - current version with which MiniBee revision F is shipped

# Loading a profile onto the XBee with X-CTU {#configure}

When you start the X-CTU software, you will see the following screen:

![](/img/x-ctu-startupscreen.png)

## Selecting the radio {#selectradio}

Click on the `Add devices` button in the upper left corner to add a new device. You will get the following dialog:

![](/img/x-ctu-add-radio-module.png)

> Note: you have to have your coordinator board with an XBee on top connected to your computer right now! If you plug it in when the dialog is already open, click on the button `Refresh ports`.


From the top half, select the Serial/USB port you want to use. On Linux, this should be something like `/dev/ttyUSB0`, on OSX something like `/dev/tty.usbserialAACC123`, on Windows something like `COM3`.

In the lower half of the dialog, you may want to change the baudrate. If the XBee has not been configured before, select `9600`. If the XBee has been used with the Sense/Stage MiniBee before, then select `57600`.

![](/img/x-ctu-choose-baudrate.png)

After selecting the USB port and checking the baudrate setting, click on the `Finish` button in the lower right corner. You will now get the following screen:

![](/img/x-ctu-discovering-radios.png)

In rare occasions, it cannot find the radio and asks you to reset the radio:

![](/img/x-ctu-action-required.png)

If this dialog shows up, push the button on the coordinator board that is at the edge under the XBee radio.

Once the radio has been found, you will see the following screen:

![](/img/x-ctu-select-radio-to-configure.png)

Click on the radio to see its configuration. You will get a popup screen telling you that it is updating the user interface and reading the radio settings:

![](/img/x-ctu-reading-radio-settings.png)

After that, it will show a list of settings in the right half of the screen.

## Selecting a profile {#selectprofile}

![](/img/x-ctu-select-profile.png)

We will now select a profile to load. Go with the mouse cursor to the `Profile` button at the top in the middle. Once you click on it, you can choose between loading and saving a profile.

![](/img/x-ctu-load-profile.png)

Click on `Load configuration profile` and browse to where you [unpacked the zip-file with the profiles](#profiles). Choose `enddevice_2017F_10ef.xml` if you want to program the XBee for use on top of the MiniBee; choose `coordinator_2017F_10ef.xml` if you want to program the XBee for use on the coordinator board that is connected to the computer.

X-CTU may give a warning that the radio firmware does not match with the profile and ask for updating:

![](/img/x-ctu-update-radio-firmware.png)

Select yes to do so, especially if it is a new version (higher number), then it will make the performance of the XBee better.

Once you have opened the configuration profile file, the list will show which settings are in the profile. The settings that are changed but not written, have a green triangle in the lower right corner.

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

Now, disconnect the coordinator node from the computer and, if you want to configure another XBee, remove the XBee and place the new XBee on top. And [start again](#configure).