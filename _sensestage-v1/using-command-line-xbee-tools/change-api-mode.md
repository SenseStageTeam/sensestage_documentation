---
title: Change API mode
summary: A guide on how to configure the XBee
layout: guide
type: guide
parent: Using command line XBee tools
guidestep: 3
creation-date: 2017-02-06
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---

  * Plug in the coordinator node with an XBee (of the coordinator or of a node) on it.
  * After starting the xbee serial terminal, selecting the baudrate and serial port and entering the AT command line mode:

  * Change to API mode:
  
    `xbee% ATAP 2`
    
  * Change the node id (for a node, not for coordinator):
  
    `xbee% ATMY FFFA`
    
  * Write the changes:
  
    `xbee% ATWR`
    
  * Repeat these steps for each XBee
