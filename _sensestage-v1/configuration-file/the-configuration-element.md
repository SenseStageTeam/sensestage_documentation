---
title: The configuration element
summary: An overview of configuration file that the communication software uses
layout: reference
type: reference
guidestep: 2
parent: Configuration file
featured-image: 

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


An example of a configuration element:

    <configuration id="2" name="environment" message_interval="50" samples_per_message="1" redundancy="3">
        <pin id="A0" config="AnalogIn" name="light" />
        <twi id="1" device="ADXL345" name="accelero"/>
    </configuration>

So top level, defined within the `<configuration>` element:

- *ID* – a unique number (i.e. no other configuration in the xml file can have the same number)
- *label* – a user friendly name or label for this configuration
- *Message interval in milliseconds* – update rate for the data, i.e. how often the MiniBee will send data. Currently the maximum (which is found to work properly) is 100 ms.
- *Samples per message (should be 1 for now)* – If this is higher than 1, the MiniBee will make measurements as often as you set the number to, and then send a package with all the data once every each message interval has passed. The time in between is divided up, so if you have a message interval of 100 and 10 sampes per message, the data is measured every 10 ms, but only sent every 100 ms.
- *Redundancy* specifies how often a message is sent to the MiniBee, when the MiniBee has outputs defined.

Then for each pin, as subelements before the closing `</configuration>`:

- *id* – this should be one of: A0, A1, A2, A3, (A4, A5,) A6, A7, D2, D3, D5, D6, D7, D8, D9, D10, D11 (see the [note on D2 and D7](d2-and-d7-for-revision-f))
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

