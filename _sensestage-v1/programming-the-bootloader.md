---
title: Programming the bootloader
summary: This page describes how to program the bootloader onto a MiniBee board
layout: documentation
type: guide
creation-date: 2017-02-06
tags: 
    - expert
    - todo
category: firmware
subcategory: arduino-ide
---

**this page is still under construction!**

*below is just a quick copy-and-paste from the old site*


If you want to reprogram the bootloader, or bypass the bootloader alltogether, with an AVR programmer you can use the pins that are broken out in the middle of the board (RX, TX, GND, 3v3, D11, D12, D13).
  
There is a special programming board availabe upon request for this purpose.

Also note that if you have a verison of the MiniBee with the ATmega328 chip (if you bought it in 2011 or 2012), and you need to upload the bootloader again or want to put code on there without the bootloader, you need to choose _Sense Stage MiniBee revD1 (3.3V, 12MHz), w/ ATmega328_ as the board, and adapt your avrdude.conf file, as described [at the bottom of this page](preparing-the-arduino-ide-for-use-with-sensestage).

<div id="attachment_875" style="max-width: 339px" class="wp-caption aligncenter">
  <a href="http://docs.sensestage.eu/wp-content/uploads/2011/09/programmerboard1.png"><img src="http://docs.sensestage.eu/wp-content/uploads/2011/09/programmerboard1.png" alt="" title="programmerboard" width="329" height="416" class="size-full wp-image-875" srcset="https://docs.sensestage.eu/old/wp-content/uploads/2011/09/programmerboard1.png 329w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/programmerboard1-237x300.png 237w, https://docs.sensestage.eu/old/wp-content/uploads/2011/09/programmerboard1-200x252.png 200w" sizes="(max-width: 329px) 100vw, 329px" /></a>
  
  <p class="wp-caption-text">
    Programmer board for the MiniBee
  </p>
</div>



## rev A

Before the firmware can be uploaded to the board, a bootloader needs to be present on the board. This section describes how the bootloader can be programmed onto the board. This only needs to be done once; depending on how you obtained your board, the bootloader may already have been programmed onto the board.

  * Soldering 
      * 2 pin female header to RX/TX
      * 2 pin female header to 3.3V / GND
      * female headers to pin D11, D12, D13
  * You need: 
      * A programmer board to fit the board on
      * A USB adapter
      * AVR mkII &#8211; avr programmer
  * While programming the bootloader, you must hold a wire to the reset pin. This is to work around an omission in the revA design.
  * Use the Arduino programming software 
      * Set the board type to _LilyPad Arduino w/ ATmega 168_.
      * Choose &#8220;Program Bootloader&#8221; with &#8220;AVR ISP mkII&#8221;
      * On Ubuntu Linux you must run the Arduino software as root in order to do this




