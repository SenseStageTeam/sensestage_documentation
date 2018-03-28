---
title: Uploading firmware to a MiniBee
summary: This page describes how to upload firmware to the MiniBee
layout: documentation
type: guide
parent: uploading-firmware-to-a-minibee
step: 0
featured-image: feature-thumb4.jpg

creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: arduino-ide
---



* Loading new firmware to the board

* Using the coordinator as a programmer

* uploading firmware (different revisions of boards!; will also have different revision of Arduino IDE)


<<<<<<< HEAD
[old website - uploading firmware](https://docs.sensestage.eu/programming-new-firmware-onto-the-minibee)
=======
**This page is still under construction!!**
*below is just a quick copy-and-paste from the old site*

## rev B, D & F

When you buy the Sense/Stage MiniBee revision D, it comes with the default firmware preloaded. In case you want to change the firmware, or update it to the latest version, read this document.

The SenseStage MiniBee can be programmed from the [Arduino software](http://arduino.cc/en/Main/Software). After you have [prepared the Arduino IDE for use with the Sense/Stage MiniBees](preparing-the-arduino-ide-for-use-with-sensestage), you have to select the following board (in the Tools->Boards -menu): 

  * rev D: _Sense Stage MiniBee revB/D (3.3V, 12MHz), w/ ATmega328p_
  * rev B: _Sense Stage MiniBee revB/D (3.3V, 12MHz), w/ ATmega328p_
  * rev A: _Sense Stage MiniBee revA (3.3V, 8MHz), w/ ATmega168_, _Arduino Pro or Pro Mini_, or _LilyPad_ (8MHz, 3.3V, ATmega 168).

The Sense/Stage MiniBee Firmware examples will show up in the File -> Examples -> MiniBee, and the MiniBee Firmware library will show up in Sketch -> Import Library… -> MiniBee.

To prepare the hardware for uploading the firmware, follow these steps (this description applies to MiniBee revision D; revision B has the RX/TX pins only broken out in the middle of the board):

  * Create a four wire cable to go between your coordinator node and the MiniBee
  * Add a four pin female header to your coordinator node
  * Remove the XBee from the coordinator node
  * Remove the XBee from the MiniBee
  * Attach the cable between the coordinator node and the MiniBee
  * Use the Arduino IDE to upload the firmware [(see here for a description of how to prepare the IDE)](preparing-the-arduino-ide-for-use-with-sensestage)
  * Note that you should not wait too long between plugging in the cable and uploading the firmware, since otherwise the MiniBee will not be in bootloader mode anymore.

## Create a four wire cable

You need a four wire cable that on one side has a four pin, 1 row header, and on the other end a four pin, 2 row header (so 2&#215;2 pins).

The pin order for the one row header is (to be connected to the coordinator node):
  
DIN &#8211; DOUT &#8211; 3.3V &#8211; GND

The pin order for the MiniBee is:
  
GND &#8211; RX
  
3v3 &#8211; TX

DIN will connect to RX, DOUT to TX. It is recommended to use a clear color coding for the wires. E.g. in the photographs below: red = 3v3, black = GND, yellow = DIN/RX, pink = DOUT/TX.

<div id="attachment_867" style="max-width: 501px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6810.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6810.jpg" alt="" title="programming the minibee with the coordinator node" width="491" height="368" class="size-full wp-image-867" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6810.jpg 491w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6810-300x224.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6810-200x149.jpg 200w" sizes="(max-width: 491px) 100vw, 491px" /></a>
  
  <p class="wp-caption-text">
    Programming the minibee with the coordinator node
  </p>
</div>

<div id="attachment_1052" style="max-width: 310px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/minibee_program_df1.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/minibee_program_df1-300x225.jpg" alt="" title="minibee_program_df1" width="300" height="225" class="size-medium wp-image-1052" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df1-300x225.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df1-1024x768.jpg 1024w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df1-200x150.jpg 200w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df1-999x749.jpg 999w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df1.jpg 1408w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Programming the MiniBee with the DFRobot coordinator node
  </p>
</div>

<div id="attachment_1053" style="max-width: 310px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/minibee_program_df2.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/minibee_program_df2-300x225.jpg" alt="" title="minibee_program_df2" width="300" height="225" class="size-medium wp-image-1053" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df2-300x225.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df2-1024x768.jpg 1024w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df2-200x150.jpg 200w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df2-999x749.jpg 999w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/minibee_program_df2.jpg 1408w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Programming the MiniBee with the DFRobot coordinator node
  </p>
</div>

## Add a four pin female header to your coordinator node

Add a four pin female header (socket, right angle) on the bottom of the coordinator node, to the pins that are labeled DIN, DOUT, GND, 3v3.

<div id="attachment_869" style="max-width: 501px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6812.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6812.jpg" alt="" title="Close up of the coordinator node connection" width="491" height="368" class="size-full wp-image-869" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6812.jpg 491w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6812-300x224.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6812-200x149.jpg 200w" sizes="(max-width: 491px) 100vw, 491px" /></a>
  
  <p class="wp-caption-text">
    Close up of the coordinator node connection
  </p>
</div>

<div id="attachment_870" style="max-width: 501px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6813.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6813.jpg" alt="" title="Close up of the MiniBee connections" width="491" height="368" class="size-full wp-image-870" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6813.jpg 491w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6813-300x224.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6813-200x149.jpg 200w" sizes="(max-width: 491px) 100vw, 491px" /></a>
  
  <p class="wp-caption-text">
    Close up of the MiniBee connections
  </p>
</div>

<div id="attachment_868" style="max-width: 501px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6811.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/IMG_6811.jpg" alt="" title="Programming the MiniBee with the coordinator node" width="491" height="368" class="size-full wp-image-868" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6811.jpg 491w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6811-300x224.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/IMG_6811-200x149.jpg 200w" sizes="(max-width: 491px) 100vw, 491px" /></a>
  
  <p class="wp-caption-text">
    Programming the MiniBee with the coordinator node
  </p>
</div>

Alternately, you can use an[Arduino Mini USB adapter](http://arduino.cc/en/Main/MiniUSB) or an Arduino board with a USB connector to upload the firmware, as shown in the pictures below, for MiniBee revision A.

<div id="attachment_368" style="max-width: 310px" class="wp-caption alignnone">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2010/06/programMiniBee.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2010/06/programMiniBee-300x128.jpg" alt="" title="programMiniBee" width="300" height="128" class="size-medium wp-image-368" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2010/06/programMiniBee-300x128.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/programMiniBee-200x85.jpg 200w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/programMiniBee.jpg 800w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Uploading the firmware to the MiniBee from the Mini USB adapter
  </p>
</div>

<div id="attachment_364" style="max-width: 310px" class="wp-caption alignnone">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2010/06/minibee_program_arduino_small.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2010/06/minibee_program_arduino_small-300x225.jpg" alt="" title="minibee_program_arduino_small" width="300" height="225" class="size-medium wp-image-364" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2010/06/minibee_program_arduino_small-300x225.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/minibee_program_arduino_small-200x150.jpg 200w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/minibee_program_arduino_small.jpg 800w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Uploading the firmware to the MiniBee using an Arduino board
  </p>
</div>


## rev A


When you buy the Sense/Stage MiniBee revision D, it comes with the default firmware preloaded. In case you want to change the firmware, or update it to the latest version, read this document.

The SenseStage MiniBee can be programmed from the [Arduino software](http://arduino.cc/en/Main/Software). After you have [prepared the Arduino IDE for use with the Sense/Stage MiniBees](preparing-the-arduino-ide-for-use-with-sensestage), you have to select the following board (in the Tools->Boards -menu): 

  * rev D: _Sense Stage MiniBee (3.3V, 12MHz), w/ ATmega328p_
  * rev B: _Sense Stage MiniBee (3.3V, 12MHz), w/ ATmega328p_
  * rev A: _Sense Stage MiniBee (3.3V, 8MHz), w/ ATmega168_, _Arduino Pro or Pro Mini_, or _LilyPad_ (8MHz, 3.3V, ATmega 168).

The Sense/Stage MiniBee Firmware examples will show up in the File -> Examples -> MiniBee, and the MiniBee Firmware library will show up in Sketch -> Import Library… -> MiniBee.

You will need either an [Arduino Mini USB adapter](http://arduino.cc/en/Main/MiniUSB) or an Arduino board with a USB connector to upload the firmware, or you can [use the coordinator node, as described on this page](programming-new-firmware-onto-the-minibee).

<div id="attachment_368" style="max-width: 310px" class="wp-caption alignnone">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2010/06/programMiniBee.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2010/06/programMiniBee-300x128.jpg" alt="" title="programMiniBee" width="300" height="128" class="size-medium wp-image-368" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2010/06/programMiniBee-300x128.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/programMiniBee-200x85.jpg 200w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/programMiniBee.jpg 800w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Uploading the firmware to the MiniBee from the Mini USB adapter
  </p>
</div>

<div id="attachment_364" style="max-width: 310px" class="wp-caption alignnone">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2010/06/minibee_program_arduino_small.jpg"><img src="http://docs.sensestage.eu/wp-content/uploads/2010/06/minibee_program_arduino_small-300x225.jpg" alt="" title="minibee_program_arduino_small" width="300" height="225" class="size-medium wp-image-364" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2010/06/minibee_program_arduino_small-300x225.jpg 300w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/minibee_program_arduino_small-200x150.jpg 200w, https://docs.sensestage.eu/old/wp-content/uploads/2010/06/minibee_program_arduino_small.jpg 800w" sizes="(max-width: 300px) 100vw, 300px" /></a>
  
  <p class="wp-caption-text">
    Uploading the firmware to the MiniBee using an Arduino board
  </p>
</div>
>>>>>>> 6a08534b698615633523078df0e7b2e0343bd5f1
