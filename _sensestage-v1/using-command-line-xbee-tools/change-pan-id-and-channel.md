---
title: Change PAN ID and channel
summary: A guide on how to configure the XBee
layout: guide
type: guide
parent: Using command line XBee tools
guidestep: 1
creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---

  * Plug in the coordinator node with an XBee (of the coordinator or of a node) on it.
  * After starting the xbee serial terminal, selecting the baudrate and serial port and entering the AT command line mode:


  * Check the channel: 
  
    `xbee% ATCH`, followed by enter. The program will show the value, e.g. `C`
  
  * Check the pan id: 
  
    `xbee% ATID`, followed by enter. The program will show the value, e.g. `1152`
  
  * Now take off the XBee from the coordinator node, put it aside, and put the XBee for a minibee on there that is not currently communicating with the coordinator node.
  
  * Enter AT command mode: 
  
    `xbee% +++` and wait for `OK`
  
  * Change the channel: 
  
    `xbee% ATCH C` &#8211; of course if your check above returned a different channel, then use that!
  
  * Change the channel: 
  
    `xbee% ATID 1152` &#8211; of course if your check above returned a different pan id, then use that!
  
  * Write the changes: 
  
    `xbee% ATWR`
  
  * Repeat these steps for each XBee you want to reconfigure
  
**NOTE: the XBees for the nodes (MiniBees) will be in sleep mode on a regular coordinator USB board, so to reprogram you need to solder a connection between DTR and GND on the coordinator USB board.**
