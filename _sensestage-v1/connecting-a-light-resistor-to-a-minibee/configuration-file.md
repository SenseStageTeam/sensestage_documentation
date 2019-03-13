---
title: Configuration file
summary: A simple tutorial on how to connect a light sensor to a MiniBee and get the data from it into your software.

parent: Connecting a light resistor to a MiniBee
layout: guide
guidestep: 3

type: guide
level: basics
priority: 20

featured-image:
creation-date: 2018-02-06
category: introduction
subcategory: tutorials
related:
    - XPee
    - XPree
tags:
    - basics
    - sensors

status: complete
---

Now that we have our electronics set up, we need to adapt the configuration file for our minibee. Let’s assume that we already have a configuration file that we used with our MiniBee, before we had attached any sensors to it.

If you started from the `example_hiveconfig.xml` configuration file, it will look like this, when you open it in a text editor.


    <xml>
    <hive name="myprojectname">

    <minibee id="1" revision="D" serial="0013A200403BF27B" libversion="6" caps="7" configuration="1">
    </minibee>

    <configuration id="1" name="accelero" message_interval="50" samples_per_message="1">
    <pin config="TWIData" id="A4" />
    <pin config="TWIClock" id="A5" />
    <twi id="1" device="ADXL345" name="accelero" />
    </configuration>

    <configuration id="2" name="expee" message_interval="50" samples_per_message="1">
    <pin config="TWIData" id="A4" />
    <pin config="TWIClock" id="A5" />
    <pin config="AnalogIn10bit" id="A0" name="analog0" />
    <pin config="AnalogIn10bit" id="A1" name="analog1" />
    <pin config="AnalogIn10bit" id="A2" name="analog2" />
    <pin config="AnalogIn10bit" id="A3" name="analog3" />
    <pin config="AnalogOut" id="D9" name="led0" />
    <pin config="AnalogOut" id="D10" name="led1" />
    <pin config="AnalogOut" id="D11" name="led2" />
    <pin config="AnalogOut" id="D3" name="led3" />
    <pin config="AnalogOut" id="D5" name="led4" />
    <pin config="AnalogOut" id="D6" name="led5" />
    <twi id="1" device="ADXL345" name="accelero" />
    </configuration>

    <configuration id="3" name="expree" message_interval="50" samples_per_message="1">
    <pin config="TWIData" id="A4" />
    <pin config="TWIClock" id="A5" />
    <pin config="AnalogIn10bit" id="A0" name="analog0" />
    <pin config="AnalogIn10bit" id="A1" name="analog1" />
    <pin config="AnalogIn10bit" id="A2" name="analog2" />
    <pin config="AnalogIn10bit" id="A3" name="analog3" />
    <pin config="AnalogIn10bit" id="A6" name="analog4" />
    <pin config="AnalogIn10bit" id="A7" name="analog5" />
    <pin config="DigitalIn" id="D3" name="digitaal0" />
    <pin config="DigitalIn" id="D5" name="digitaal1" />
    <pin config="DigitalIn" id="D6" name="digitaal2" />
    <pin config="DigitalIn" id="D7" name="digitaal3" />
    <pin config="DigitalIn" id="D8" name="digitaal4" />
    <pin config="DigitalIn" id="D9" name="digitaal5" />
    <pin config="DigitalIn" id="D10" name="digitaal6" />
    <pin config="DigitalIn" id="D11" name="digitaal7" />
    <twi id="1" device="ADXL345" name="accelero" />
    </configuration>

    </hive>
    </xml>

We will add a new configuration element to it:


    <configuration id="4" name="lightsensor" message_interval="50" samples_per_message="1">
    <pin config="AnalogIn10bit" id="A0" name="light" />
    <twi id="1" device="ADXL345" name="accelero"/>
    </configuration>

This defines pin A0 to be read as an analog input with a 10 bit resolution. It also keeps the accelerometer active.

Then we need to assign our MiniBee to use this configuration:


    <minibee id="1" revision="D" serial="0013A200403BF27B" libversion="6" caps="7" configuration="4">
    </minibee>

Note that in the configuration setting we now point to configuration number 4.

Now save the configuration file with a new filename (e.g. `lightsensor.xml`)

Then we can start pydongui.py and use our new configuration file.

Then if we turn on our MiniBee, it will be assigned the new configuration, and send out the data as follows:


    "/minibee/data" id lightsensor acceleration-x acceleration-y acceleration-z

All are values between 0 and 1.
