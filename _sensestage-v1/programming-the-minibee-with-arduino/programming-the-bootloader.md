---
title: Programming the bootloader
summary: This page describes how to program the bootloader onto a MiniBee board
layout: guide
type: guide
parent: Programming the MiniBee with Arduino
guidestep: 4
creation-date: 2017-02-06
tags: 
    - expert
    - todo
category: firmware
subcategory: arduino-ide
---

If you want to reprogram the bootloader, or bypass the bootloader alltogether, with an AVR programmer you can use the pins that are broken out in the middle of the board (RX, TX, GND, 3v3, D11, D12, D13).
  
There is a special programming board availabe upon request for this purpose.

{:.image-caption}
![](/img/programmerboard.png)
*Programmer board for the MiniBee*


## MiniBee revision A

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
<!--      * On Ubuntu Linux you must run the Arduino software as root in order to do this-->

# TODO

- add images of AVR programmer, connections to MiniBees, pogopin boards