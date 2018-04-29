---
title: Loading a profile
summary: A guide on how to configure the XBee

layout: guide
type: guide
parent: Adding New Minibees to a Network
guidestep: 5

creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---

# Getting the XBee profiles for the Sense/Stage MiniBee {#profiles}

The XBee profiles for Sense/Stage are available from [this git repository](https://github.com/sensestage/ssdn_xbee). Click on the `Clone or Download` button, or use this [direct link for a zip-file](https://github.com/sensestage/ssdn_xbee/archive/master.zip).

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


We will now select a profile to load. Go with the mouse cursor to the `Profile` button at the top in the middle. Once you click on it, you can choose between loading and saving a profile.

![](/img/x-ctu-select-profile.png)

![](/img/x-ctu-load-profile.png)

Click on `Load configuration profile` and browse to where you [unpacked the zip-file with the profiles](#profiles).

* Choose `enddevice_2017F_10ef.xml` if you want to program the XBee for use on top of the MiniBee
* Choose `coordinator_2017F_10ef.xml` if you want to program the XBee for use on the coordinator board that is connected to the computer.

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
