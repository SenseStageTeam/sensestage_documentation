---
title: Connecting a MiniBee for the first time
summary: A guide on how to configure a MiniBee for the first time
layout: documentation
type: guide
date: 2017-02-06
tags:
    - basics
    - configuration
    - todo
category: introduction
subcategory: getting-started
related:
    - Power supply
    - LED blinking codes
    - Using the Hive
    - Configuration file
---

Once you have installed the software, you can connect a MiniBee for the first time:

# Start the software

The software can be started in the following ways:

- On Linux and OSX from the commandline with `pydongui.py`
- On Windows you can start it by double clicking on the file `start_pydon.bat`

In the window you have to configure a few settings:

* select mode (OSC)
* select usb port
    * on Linux: something like: `/dev/ttyUSB0` or `/dev/ttyACM0`
    * on OSX: something like: `/dev/tty-usb.serialAACC6789`
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

A green LED, the middle one in the row of three next to the power switch will light up. After a few seconds, an orange LED will start blinking, indicating that the radio is active. After a while a red LED will turn on momentarily, indicating that the MiniBee is receiving data from the coordinator node. The software sends a message to assign the MiniBee an ID. At the coordinator node, you will notice that the RX/TX LEDs start blinking as well.


> *insert pictures here to show the blinking lights*

> [More details on the LEDs](led-blinking-codes)


You will also see a message in the logging window of the software saying something like:

    ('no configuration defined for minibee', '0013A20040AA4ECC', 1, '')
    configuration saved to newconfig_2017_Jan_19_18-03-55.xml. Please adapt (at least define a config id other than -1 for the node), save to a new name, and restart the program with that configuration file. Alternatively send a message with a new configuration (via osc, or via the datanetwork).
    Check documentation for details.


# Configuring the minibee

The software has created a new configuration file in the directory from which you started the software. In our example the file has the name `newconfig_2017_Jan_19_18-03-55.xml`. The filename is automatically generated from the date and time of the computer. If you open the file with a plain text editor, it will look like this:

> *give suggestions for programs to open the file with on different platforms!*

> On Linux use a plain text editor like MousePad, gedit or kwrite for reading the file. 


```
<?xml version="1.0" ?>
<xml>
  <hive name="myprojectname">
    <minibee caps="7" configuration="-1" id="1" libversion="7" name="" revision="D" serial="0013A20040AA4ECC">
      <!--the id given inside the minibee tag is the unique id or number of the minibee-->
      <!--the configutaion inside the minibee tag is the unique id of the configuration that is used. It has to match one of the configuration id's that are defined in this file.-->
      <!--This minibee has no configuration yet! Change it to use one of the configurations in this file.-->
    </minibee>
    <configuration id="1" message_interval="50" name="accelero" redundancy="3" rssi="False" samples_per_message="1">
      <pin config="TWIClock" id="A5" name="None"/>
      <pin config="TWIData" id="A4" name="None"/>
      <twi device="ADXL345" id="1" name="accelero"/>
    </configuration>
  </hive>
</xml>
```

You will see two main elements in the file, one called `minibee` and three called `configuration` (in the output above, I just show one of the example configurations). The file shows a warning that the minibee has no configuration yet:

    <!--This minibee has no configuration yet! Change it to use one of the configurations in this file.-->

We can give it a configuration by changing the line:

    <minibee caps="7" configuration="-1" id="1" libversion="7" name="" revision="D" serial="0013A20040AA4ECC">

to

    <minibee caps="7" configuration="1" id="1" libversion="7" name="" revision="D" serial="0013A20040AA4ECC">

So instead of `configuration="-1"` we have `configuration="1"`. This means that the MiniBee will be using configuration number 1. This configuration is just reading out the accelerometer.

We can now save the file to a new filename, e.g. `myfirstminibee.xml`.

> [More details on the configuration file](configuration-file)


# Stop and restart the software

Now stop the communication of the software by hitting the `[STOP]` button. Then change the configuration file to use to the file you just saved. Then press the button `[START]` again.

Now, after a short time, the MiniBee will be detected again. The red light on the MiniBee will turn on again, and the RX/TX LEDs on the coordinator will blink. The following text will be output in the window, to indicate that the MiniBee is configured:

    ('confirmconfig', [1, 0, 50, 6, 0, 0, 0])
    minibee 1 is configured

Once you see this message, the OSC data will be sent out to the IP-address and port that you defined in the startup settings.


# TODO

- insert pictures