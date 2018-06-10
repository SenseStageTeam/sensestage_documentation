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

In order to program a MiniBee you'll need a programmer with wires connected to the MiniBee's GND, 3v3, RX and TX pins. You can most easily use the [coordinator board](/sensestage-v1/coordinator-board/) of your Sense/Stage network to do the programming. This is the method that will be shown in this guide. This guide assumes you are able to do some basic soldering in order to make the four-wire programming cable.

> Note: This guide applies to the latest MiniBee revisions __F__ and __D__; see the [MiniBee board reference](/sensestage-v1/minibee-board-reference/) if you are unsure which revision you have. The earlier revision __B__ boards have the RX/TX pins only broken out in the middle of the PCB.*

# Creating the four wire serial cable

In order to connect the coordinator board to your MiniBee's GND, 3v3, RX and TX pins you will need to create a four-wire connection between the coordinator and the minibee. You could do this using loose jumper cables and a bit of soldering, but we prefer to make a custom cable that can easily be removed.

In order to make the four-wire cable you'll need the following materials, note that all pin headers have 2.54mm pin spacing:

* a 4x1 pin male header
* a 2x2 pin male header
* an angled 4x1 pin female header (to attach to the coordinator)
* a four wire ribbon cable, or four pieces of hookup wire

![](/img/programmer/fourwire-materials-01.jpg)
*The materials you'll need*

## First, solder the angled female header to these four pins.

Looking under the coordinator board, you'll see all the through-hole solder pins marked. The four pins you will connect to on the coordinator board are __GND 3.3V DOUT__ and __DIN__ ~ connect the 4-pin header to these pins.

![](/img/programmer/fourwire-coord-femheader-02.jpg)
*4-pin female header soldered to the GND, 3.3V, DOUT and DIN pins of the coordinator*

## Making the connecting cable

Now you'll need to make a cable connecting these four pins to four pins on the MiniBee. If you look under the MiniBee (where the header attaches) you'll see the pins labeled. The pins you will connect to on the MiniBee are __GND VCC TX__ and __RX__ ~ these four pins are in a 2x2 pattern, which you will use the 2x2 header to connect into.

![](/img/programmer/minibee-header-annotated.jpg)

Go ahead and solder the cable. Be very careful that the wires are connected correctly at the two ends. We also recommended that you use a clear color coding for the wires. In the photographs below, we are using: red = 3v3, black = GND, orange = DOUT/TX, yellow = DIN/RX.

Make the pin connections from the coordinator to the MiniBee as follows:

__GND   ->  GND__

__3.3V  ->  VCC__

__DOUT  ->  TX__

__DIN   ->  RX__



![](/img/programmer/fourpin-header-annotated.jpg)
*Wires attached to the 2x2 header*

![](/img/programmer/minibee-coordinator-unplugged.jpg)
*The finished cable, connecting the coordinator to the MiniBee*

## Connect the Coordinator to your computer

Now that you've made the serial programmer cable. Connect the coordinator to your computer's USB port, and connect the MiniBee to the coordinator using the cable you just made. The MiniBee's green power LED should turn on, indicating that it is receiving power from the coordinator board.

![](/img/programmer/minibee-coordinator-plugged.jpg)


In the [next step](prepare-the-arduino-ide) you'll configure the Arduino IDE with appropriate hardware profiles to be able to detect and program your MiniBees.



<!--
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

-->
