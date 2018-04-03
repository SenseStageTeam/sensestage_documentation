---
title: Change power level
summary: A guide on how to configure the XBee
layout: guide
type: guide
parent: Using command line XBee tools
guidestep: 2
creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---

  * Plug in the coordinator node with an XBee (of the coordinator or of a node) on it.
  * After starting the xbee serial terminal, selecting the baudrate and serial port and entering the AT command line mode:

  * Query the current power level: 
  
    `xbee% ATPL`

  * Change the power level: 
  
    `xbee% ATPL 0`
    
  * Write the changes: 
  
    `xbee% ATWR`
    
  * Repeat these steps for each XBee (Pro)
