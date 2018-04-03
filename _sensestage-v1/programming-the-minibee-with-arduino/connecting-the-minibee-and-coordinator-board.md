---
title: Connecting the MiniBee and coordinator board
summary: This page describes how to create a connection between the MiniBee and coordinator board to program the minibee
layout: guide
type: guide
parent: Programming the MiniBee with Arduino
guidestep: 1
creation-date: 2017-02-06
tags: 
    - expert
    - todo
category: firmware
subcategory: arduino-ide
---

To prepare the hardware for uploading the firmware, a four wire connection needs to be created between the MiniBee and the coordinator board. 

*This description applies to MiniBee revision [F](../minibee-types/revision-f) and [D](../minibee-types/revision-d); [revision B](../minibee-types/revision-b) has the RX/TX pins only broken out in the middle of the board.*

* Create a [four wire cable](#fourwire) to go between your coordinator node and the MiniBee
* Add a four pin female header to your coordinator node
* Remove the XBee from the coordinator node
* Remove the XBee from the MiniBee
* Attach the cable between the coordinator node and the MiniBee


## Create a four wire cable {#fourwire}

You need a four wire cable that on one side has a four pin, 1 row header, and on the other end a four pin, 2 row header (so 2&#215;2 pins).

The pin order for the one row header is (to be connected to the coordinator node):

DIN &#8211; DOUT &#8211; 3.3V &#8211; GND

The pin order for the MiniBee is:

GND &#8211; RX
3v3 &#8211; TX

DIN will connect to RX, DOUT to TX. It is recommended to use a clear color coding for the wires. E.g. in the photographs below: red = 3v3, black = GND, yellow = DIN/RX, pink = DOUT/TX.


## Add a four pin female header to your coordinator node

Add a four pin female header (socket, right angle) on the bottom of the coordinator node, to the pins that are labeled DIN, DOUT, GND, 3v3.

{:.image-caption}
![](/img/programming_coordinator-minibee.jpg)
![](/img/programming_coordinator-minibee-2.jpg)
![](/img/programming_coordinator-minibee-3.jpg)
![](/img/programming_coordinator-minibee-4.jpg)
*Making a 4-wire-cable and a pinheader to create a connection between the Sparkfun coordinator board and the MiniBee*

{:.image-caption}
![](/img/minibee_program_df1.jpg)
![](/img/minibee_program_df2.jpg)
*Making connections with jumper wires between the DFRobot coordinator board and the MiniBee*

## Using a Arduino Mini USB adapter

Alternately, you can use an [Arduino Mini USB adapter](http://arduino.cc/en/Main/MiniUSB) or an Arduino board with a USB connector to upload the firmware, as shown in the pictures below, for MiniBee revision A.

{:.image-caption}
![](/img/minibee_revA_program-usb-adapter.jpg)
*Uploading the firmware to the MiniBee revision A from the Mini USB adapter*

{:.image-caption}
![](/img/minibee_revA_program_arduino_small.jpg)
*Uploading the firmware to the MiniBee revision A using an Arduino board*

