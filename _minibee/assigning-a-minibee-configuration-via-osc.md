---
title: Assigning a MiniBee Configuration via OSC
summary: A guide on how to assign a configuration to a MiniBee via OSC
layout: documentation
type: guide
date: 2017-02-06
tags:
    - intermediate
    - configuration
category: introduction
subcategory: getting-started
related:
    - Power supply
    - LED blinking codes
    - Using the Hive
    - OSC interface
---


Once you have installed the software, you can connect a MiniBee for the first time:

# Start the software

The software can be started in the following ways:

- On Linux and OSX from the commandline with ```pydongui.py```
- On Windows you can start it by double clicking on the file ```start_pydon.bat```

In the window you have to configure a few settings:

* select mode (OSC)
* select usb port
    * on Linux: something like: `/dev/ttySUB0` or /dev/ttyACM0`
    * on OSX: something like: '/dev/tty-usb.serialAACC6789`
    * on Windows: something like: `COM1`
* select a configuration file: from the folder `ssdn_python-master`: `examples/configuration/example_hiveconfig.xml`
* select the IP address and port to send OSC to

> [More details on the settings](using-the-hive)

# Plug in the battery

The first step is to plug in the battery to the MiniBee. The battery is connected with the JST connector.

> *insert pictures here to show the battery plugin procedure*

> [More details on powering the MiniBee](power-supply)

# Turn the minibee on

Turn on the minibee, by moving the small switch which is next to the JST connector.

A green LED, the middle one in the row of three next to the power switch will start burning. After a few seconds, an orange LED will start blinking, indicating that the radio is active. After a while a red LED will turn on momentarily, indicating that the MiniBee is receiving data from the coordinator node. The software sends a message to assign the MiniBee an ID. At the coordinator node, you will notice that the RX/TX LEDs start blinking as well.


> *insert pictures here to show the blinking lights*

> [More details on the LEDs](led-blinking-codes)


You will also see a message in the logging window of the software saying something like:

    ('no configuration defined for minibee', '0013A20040AA4ECC', 1, '')
    configuration saved to newconfig_2017_Jan_19_18-03-55.xml. Please adapt (at least define a config id other than -1 for the node), save to a new name, and restart the program with that configuration file. Alternatively send a message with a new configuration (via osc, or via the datanetwork).
    Check documentation for details.


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

> [Advanced guide on creating configurations via OSC](creating-minibee-configurations-via-osc)