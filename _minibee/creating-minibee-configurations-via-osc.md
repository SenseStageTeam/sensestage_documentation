---
title: Creating MiniBee configurations via OSC
summary: A guide on how to create a configuration from scratch via OSC
layout: documentation
type: guide
date: 2017-02-06
tags:
    - advanced
    - configuration
    - todo
category: software
subcategory: configuration
related:
    - OSC interface
---



# OSC information that is exchanged and configuring the minibee

During this startup procedure the hive sends out a couple of messages to the user software. As the MiniBee connects, an information message (`/minibee/info`) is sent with the serial number of the MiniBee, the ID that is assigned and the number of inputs and outputs of the MiniBee. If the MiniBee is not configured yet, the number of inputs and outputs will be 0. Also, a status message is sent (`/minibee/status`), with the ID of the MiniBee and a string indicating the status - which will be `waiting`, as it is waiting for a new configuration.

You can then send a message to the Hive to assign a configuration ID to the MiniBee. The configuration ID has to be one that is defined in the configuration file that is currently loaded. In our example configuration we have three possible configurations numbered 1, 2 and 3. So these are the numbers we can assign. If we send a message:
    
    /minibee/configuration 1 1

then MiniBee 1 is assigned configuration 1.

The hive sends a message back to confirm (`/minibee/configuration/done`) or to indicate an error (`/minibee/configuration/error`).

Now, communication between the coordinator and the MiniBee is happening again. The red light on the MiniBee will turn on again, and the RX/TX LEDs on the coordinator will blink. The following text will be output in the window, to indicate that the MiniBee is configured:

    ('confirmconfig', [1, 0, 50, 6, 0, 0, 0])
    minibee 1 is configured

And a new info-message is sent, indicating that the MiniBee has 3 inputs (the three axes of the accelerometer). And status updates are sent: first that the MiniBee is `configured`, then that we are `receiving` data from it.
    
Once you see this message, the OSC data will be sent out with `/minibee/data` messages.

# Saving the configuration

We can then save the configuration we made to file, so we can load it again later on, by sending a message `/minihive/configuration/save` with a filename as argument. The filename is relative to the folder `pydongui.py` was started from. For example we can send:

    /minihive/configuration/save myoscconfig.xml

to save it to a file name `myoscconfig.xml`

> [More details on the OSC interface](osc-interface)

# TODO

- rewrite this page
