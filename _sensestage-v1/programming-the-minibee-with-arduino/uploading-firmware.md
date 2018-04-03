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

Select your board (in the `Tools->Boards`-menu) of the Arduino IDE:

* for revisions F, D or B: Sense/Stage MiniBee revB/D/F (3.3V, 12MHz) w/ Atmega328p
* for revision A: Sense/Stage MiniBee revA (3.3V, 8MHz) w/ Atmega168 (alternately you can choose: _Arduino Pro or Pro Mini_, or _LilyPad_ (8MHz, 3.3V, ATmega 168).

The Sense/Stage MiniBee Firmware examples will show up in the `File -> Examples -> MiniBee_APIn`, and the MiniBee Firmware library will show up in `Sketch -> Import Library… -> MiniBee_APIn`.

Once your firmware is ready:

* click **[Compile]** to check the firmware, fix any errors if they show up in the Arduino post window at the bottom.
* click **[Upload]** to upload the firmware.

> Don't wait too long between plugging in the cable and uploading the firmware, since otherwise the MiniBee will not be in bootloader mode anymore. To be able to this quick enough, you might want to use the keyboard shortcut **[CTRL-U]** for uploading in the Arduino IDE.



