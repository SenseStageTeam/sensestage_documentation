---
title: Making your first Configuration File
summary: A guide on how to make a configuration file for your network. This example shows a network created using two sensor nodes.

layout: guide
type: guide
parent: Getting Started with Sense Stage
guidestep: 4

creation-date: 2017-02-06
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

Once you have installed Pydon and any drivers necessary to detect the coordinator, the next step is to set up your first sensor network configuration. At this point it may be worthwhile refreshing yourself on the different components of a [Sense/Stage wireless setup](/sensestage-v1/overview-of-the-system).

You will need to create a Pydon configuration file with information about each of the nodes (MiniBees) in your network. This configuration file includes which sensors and input/output pins are active on each node.

This process can be a bit confusing for first-time users. If you have trouble following the process outlined below then you may want to follow one of our video tutorials on making your first network configuration.
* [Creating your first Configuration on Windows](https://vimeo.com/272595238)
* [Creating your first Configuration on OS X]()

# 1. Start Pydon

Pydon can be started in the following ways:

- On Linux and OSX from the command line with `pydongui.py`
- On Windows you can start it by double clicking on the file `start_pydon.bat`

In the window you have to configure a few settings:

* select mode (OSC or Junxion)
* select usb port
    * on Linux: something like: `/dev/ttyUSB0` or `/dev/ttyACM0`
    * on OSX: something like: `/dev/tty-usbserial-AACC6789` or `/dev/cu.usbmodem14211`
    * on Windows: something like: `COM1`
* select a configuration file: a good starting point is to use the `example_hiveconfig.xml` from the examples folder in the Pydon package: `examples/configuration/example_hiveconfig.xml`
* select the IP address and port of the program that Pydon should send OSC data to

> [More details on the settings](/sensestage-v1/pydon-software-reference)

# 2. Plug in the batteries to your MiniBees

Plug in the battery to your MiniBees. Most likely you are using a rechargeable 3.7 volt LiPo battery, with a JST-PH 2mm connector on it that will fit the connector on the MiniBee.

![](minibee-lipo-connect-05.jpg)
*MiniBee with LiPo battery connected*

> [Guide to safe battery handling](/sensestage-v1/guide-to-batteries)

> [More details on powering the MiniBee](/sensestage-v1/power-supply)

# 3. Turn the MiniBee on

Turn on the minibee, by moving the small switch which is next to the JST connector.

A green LED, the middle one in the row of three next to the power switch will light up. After a few seconds, an orange LED will start blinking, indicating that the radio is active. After a while a red LED will turn on momentarily, indicating that the MiniBee is receiving data from the coordinator. The software sends a message to assign the MiniBee an ID. At the coordinator node, you will notice that the RX/TX LEDs start blinking as well.

> [More details on the Minibee's LEDs](/sensestage-v1/led-blinking-codes)


You will also see a message in Pydon's feedback window saying something like:

    ('no configuration defined for minibee', '0013A20040AA4ECC', 1, '')
    configuration saved to newconfig_2017_Jan_19_18-03-55.xml. Please adapt (at least define a config id other than -1 for the node), save to a new name, and restart the program with that configuration file. Alternatively send a message with a new configuration (via osc, or via the datanetwork).
    Check documentation for details.


# 4. Create a Configuration Entry for the MiniBee

The software has created a new configuration file in the directory from which you started the software. In our example the file has the name `newconfig_2017_Jan_19_18-03-55.xml`. The filename is automatically generated from the date and time of the computer. If you open the file with a plain text editor, it will look like this:

> On OS X and Windows, two good free options for basic text editors are [Sublime Text](https://www.sublimetext.com/) and [Atom](https://atom.io/).

> On Linux you can use a plain text editor like MousePad, gedit or kwrite for reading the file.


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

> [More details on the configuration file](/sensestage-v1/configuration-file)


# 5. Stop and Restart Pydon with your New Configuration File

Now stop the communication of the software by hitting the `[STOP]` button. Then change the configuration file to use to the file you just saved. Then press the button `[START]` again.

Now, after a short time, the MiniBee will be detected again. The red light on the MiniBee will turn on again, and the RX/TX LEDs on the coordinator will blink. The following text will be output in the window, to indicate that the MiniBee is configured:

    ('confirmconfig', [1, 0, 50, 6, 0, 0, 0])
    minibee 1 is configured

Once you see this message, the OSC data will be sent out to the IP-address and port that you defined in the startup settings.
