---
title: Uploading firmware
summary: This page describes how to upload firmware to the MiniBee
layout: guide
type: guide
parent: Programming the MiniBee with Arduino
guidestep: 3
featured-image: feature-thumb4.jpg

creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: arduino-ide
---

At this point you have made a programming cable and have added the Sense/Stage libraries and hardware profile files to your Arduino IDE. You are ready to upload code to the MiniBee.

In the Arduino IDE, select your board (in the `Tools->Boards`-menu) of the Arduino IDE, choose 'Sense/Stage MiniBee'.

Next choose your processor in `Tools->Processor`, either:
* ATmega 328p rev B/D/F (3.3V, 12 MHz) for board revision F, D or B
* ATmega 328 rev D1 (3.3V, 12 MHz) for board revision D1
* ATmega 168 rev A (3.3V, 8 MHz) for board revision A (alternately you can choose: _Arduino Pro or Pro Mini_, or _LilyPad_ (8MHz, 3.3V, ATmega 168).

Finally, choose the USB port your programmer is connected to in `Tools->Port`.

The Sense/Stage MiniBee Firmware examples will show up in `File -> Examples -> MiniBee_APIn`, inside you will find the `minibee_F` default firmware for all new rev F boards. The MiniBee Firmware library will show up in `Sketch -> Include Library… -> MiniBee_APIn`.

Once your firmware is ready:

* click **[Compile]** to check the firmware, fix any errors if they show up in the Arduino post window at the bottom.
* disconnect the four-wire cable from the MiniBee and then plug it back in
* quickly click **[Upload]** to upload the firmware

> Note!: Don't wait too long after plugging in the cable to upload the firmware, it should be done almost immediately after plugging in the cable and providing power to the MiniBee. When it first powers up, the MiniBee is briefly in bootloader mode, which is the point when it is available for reprogramming. To be able to do this more quickly you might want to use the keyboard shortcut **[CTRL-U]** for uploading in the Arduino IDE. Another option is to attach a momentary switch to the 3.3V / VCC wire on the cable that can be used to quickly power on and off the MiniBee.

For most people, this is enough information to reprogram the MiniBee, but in rare cases you may also want to completely reprogram of bypass the bootloader. Continue on to the [next step](programming-the-bootloader) for instructions on how to do this.
