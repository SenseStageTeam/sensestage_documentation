---
title: Using command line XBee tools
permalink: /sensestage-v1/using-command-line-xbee-tools/index.html
summary: A guide on how to configure the XBee with command line tools
layout: guide
type: guide
guidestep: 0
creation-date: 2017-02-06
featured-image: feature-thumb2.jpg
tags:
    - expert
    - todo
category: firmware
subcategory: xbee
---


Instead of [X-CTU](../using-x-ctue), you might want to use a command line interface for reading or adapting the settings of an XBee.

For this, there are the python-based [XBee Tools](https://github.com/sensestage/xbee-tools) you make the changes from any computer or operating system.

Download the tools and start it with

    $ cd python
    $ python xbee-serial-terminal.py
    
A new prompt will appear `xbee% ` where you can type commands. After you typed a command, you need to press **[Enter]** to send the command to the XBee.

For all operations, you will have to set the baudrate, open the serial port, and enter the AT command mode in order to query or change settings of the XBee.
    
Select the baudrate: 

    xbee% baudrate 57600

Select the serial port (your serial path may be different!): 

    xbee% serial /dev/ttyUSB0
    
To enter AT command mode:
  
    `xbee% +++`
    
and wait for `OK`

Then you can enter different AT commands to query or change the settings of the XBee. If no command has been received for a couple of seconds, the device will leave the AT command mode again and you have to reenter it with `+++`.


When you are done with querying and changing settings you can exit the command line program with **[CTRL-C]**

And of course, after you have changed XBee settings, make sure that your coordinator XBee is on the coordinator board again, and your node XBees are on your MiniBees.
