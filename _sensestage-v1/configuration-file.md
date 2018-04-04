---
title: Configuration file
summary: This page describes the file format for the configuration of the MiniBees.
layout: documentation
type: reference
creation-date: 2017-02-06
category: software
subcategory: configuration
tags:
    - configuration
related:
    - Connecting a MiniBee for the first time
    - Basic features of the firmware
    - Assigning a MiniBee Configuration via OSC
status: complete
---

The configuration files for PydonHive use the [XML format](https://www.w3schools.com/xml/default.asp).

[Example configurations](https://github.com/sensestage/ssdn_python/blob/master/examples/configuration/) are given in the xml files you find in the `examples/configuration` folder of the package:

The top level structure is:

    <xml>
    <hive name="myprojectname">
    </hive>
    </xml>

Then there are elements for each MiniBee you have:


    <minibee id="1" revision="F" serial="0013A200406A697E" libversion="8" caps="7" configuration="1">
    </minibee>

So the ID, the revision of the board, the serial number of its XBee (see back side of XBee as in the image below; but [see also below](#autoconf) as pydonhive will find the [serial number automatically](#autoconf)), the library version and the capabilities are defined. The elements you want to change are the id, and the serial number.

![](/img/Xbee_serial.jpg)

Then you define the configuration that is used by this minibee by a number, which refers to a configuration element.

Several MiniBees can be defined that have the same configuration, e.g. minibees 1, 2 and 3 have configuration no. 1, minibees 4 and 5 have configuration no. 2, and so on.

An example of a configuration element:

    <configuration id="2" name="environment" message_interval="50" samples_per_message="1" redundancy="3" rssi="True">
        <pin id="A0" config="AnalogIn" name="light" />
        <twi id="1" device="ADXL345" name="accelero"/>
    </configuration>

So top level, defined within the `<configuration>` element:

- *ID* – a unique number (i.e. no other configuration in the xml file can have the same number)
- *label* – a user friendly name or label for this configuration
- *Message interval in milliseconds* – update rate for the data, i.e. how often the MiniBee will send data. Currently the maximum (which is found to work properly) is 100 ms.
- *Samples per message (should be 1 for now)* – If this is higher than 1, the MiniBee will make measurements as often as you set the number to, and then send a package with all the data once every each message interval has passed. The time in between is divided up, so if you have a message interval of 100 and 10 sampes per message, the data is measured every 10 ms, but only sent every 100 ms.
- *Redundancy* specifies how often a message is sent to the MiniBee, when the MiniBee has outputs defined.
- *RSSI* specifies whether or not the RSSI (received signal strength indication) data from the wireless transmission should be transmitted as data. If you want to have this data available it should be set to “True” (case-sensitive) since pydongui version 0.32 (June 2013)

Then for each pin, as subelements before the closing `</configuration>`:

- *id* – this should be one of: A0, A1, A2, A3, (A4, A5,) A6, A7, D2, D3, D5, D6, D7, D8, D9, D10, D11 (see the [note below on D2 and D7](#d2isd7))
- *label* - The label is used to create a label for the DataSlot that this pin will be providing in the DataNode corresponding to the MiniBee (when using the DataNetwork mode to communicate)
- *configuration* – Pins that are not mentioned are not configured. Possible pin configurations (use these exact names, it is case sensitive):
    * `DigitalIn` — digital input (any pin *except* for A4, A5, A6, A7)
    * `DigitalInPullup` — digital input with pullup resistor enabled (any pin *except* for A4, A5, A6, A7) since library version 6 (June 2013)
    * `DigitalOut` — digital output on/off (any pin *except* for A4, A5, A6, A7)
    * `AnalogIn` — analog input (for pin A0, A1, A2, A3, A6, A7)
    * `AnalogIn10bit` — analog input with 10bit result (for pin A0, A1, A2, A3, A6, A7)
    * `AnalogOut` — PWM or analog out (pins D3, D5, D6, D9, D10, D11)
    * `TWIClock` — Use a TWI/I2C sensor, clock signal (pin A5); this is configured automatically, if a TWI device is present in the configuration.
    * `TWIData` — Use a TWI/I2C sensor, data signal (pin A4); this is configured automatically, if a TWI device is present in the configuration.

- If TWI (two wire interface or I2C) is used: the devices which are used:

`<twi id="1" device="ADXL345" name="accelero" />`

Currently supported is only the `ADXL345`, but in [older versions of the firmware](#oldoptions) other TWI sensors were also supported. Each twi entry needs a unique number and the number will determine in which order the data will be sent out to your software:


<!--Optionally, you can define your own labels for the device, rather than the default ones, e.g.
        <twi id="1" device="ADXL345" name="accelero" >
            <twislot id="0" name="x" />
            <twislot id="1" name="y" />
            <twislot id="2" name="z" />
        </twi>-->

# Automatically generating configurations {#autoconf}

You do not need to look up and type in the serial numbers of your XBees, if start from an example configuration file, and start communicating with an unknown MiniBee, pydonhive will automatically generate a new xml file (with a name like: ```newconfig_2013_Mar_18_18-16-38.xml```, containing the basic details of the MiniBee but with a configuration ID of “-1″. Simply change the configuration ID to one that is defined in the file.

    <minibee caps="7" configuration="-1" id="3" libversion="8" name="" revision="F" serial="0013A200406A697E">
    <!--the id given inside the minibee tag is the unique id or number of the minibee-->
    <!--the configutaion inside the minibee tag is the unique id of the configuration that is used. It has to match one of the configuration id's that are defined in this file.-->
    <!--This minibee has no configuration yet! Change it to use one of the configurations in this file.-->
    </minibee>
    
Instead of editing the file, you can also [assign a configuration via OSC](assigning-a-minibee-configuration-via-osc).

## Note on D2 and D7 for MiniBee revision F {#d2isd7}

With board revision F, the connection of pin D2 to the XBee sleep pin was changed: instead pin D7 is connected to the XBee sleep pin, and pin D2 is connected to the pin header instead of D7. In order to keep backwards compatibility of expansion boards the firmware and software behave as follows:

* if pin `D2` is defined in the configuration file, then the function defined there is used
* if pin `D7` is defined in the configuration file, and no function is defined for `D2`, then the function defined for `D7` is used for pin `D2`.
* if both `D2` and `D7` are defined in the configuration file, then the function defined for `D2` is used for the pin, and the function for `D7` is ignored.
* For older minibee revisions any configuration of pin `D2` is ignored.

For revision F the software performs a check to move the configuration of pin `D2` to `D7`.

# Pin options from configurations for [older versions of the firmware](basic-features-of-the-firmware#obsolete) {#oldoptions}

As of firmware version 10, the Ping and SHT are no longer supported standard in the firmware. They are supported in firmware versions up to 8.

* `Ping` — Ultrasonic sensor (any pin *except* for A4, A5, A6, A7)
* `SHTClock` — Clock signal for SHT15 sensor (temperature/humidity) (any pin *except* for A4, A5, A6, A7)
* `SHTData` — Data signal for SHT15 sensor (temperature/humidity) (any pin *except* for A4, A5, A6, A7)

In firmware version up to 8, the following other TWI devices were supported: `LIS302DL`, `TMP102`, `BMP085` and `HMC58X3`.

An example with multiple TWI devices:

    <configuration id="2" name="environment" message_interval="50" samples_per_message="1" redundancy="3" rssi="True">
        <twi id="1" device="ADXL345" name="accelero"/>
        <twi id="2" device="TMP102" name="tmp" />
        <twi id="3" device="BMP085" name="bmp"/>
    </configuration>
