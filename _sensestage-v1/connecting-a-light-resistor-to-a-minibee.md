---
title: Connecting a light resistor to a MiniBee
summary: A simple tutorial on how to connect a light sensor to a MiniBee and get the data from it into your software.
layout: documentation
type: tutorial
creation-date: 2017-02-06
category: introduction
subcategory: tutorials
related:
    - XPee
    - XPree
tags:
    - basics
    - sensors
---


# The electronics

A light sensor is a variable resistor. In order to connect it to the MiniBee, you need to make a [voltage divider](http://en.wikipedia.org/wiki/Voltage_divider):

![](/img/voltagedivider.png){:height="220px"}


In this picture, RVAR (VARiable Resistor) is the light sensor, and R is another resistor with which you are creating the voltage divider. In this setup, the current will flow from Vcc to GND, and the voltage will be *divided* over RVAR and R. The voltage is measured by the MiniBee at A0. The voltage will vary, as RVAR will vary – in the case of our light sensor, it depends on the amount of light that is falling onto the sensor.

To calculate the best (i.e. the value that results in the widest range of voltage) value for the resistor R, you can do the following:

* Measure the value of the resistance of the light sensor in full darkness – Rdark
* Measure the value of the resistance of the light sensor in full brightness – Rlight
* Multiply the two values measured (Rdark * Rlight)
* Take the square root of this
* Take a resistor that has a resistance value close to this calculated value

As an example, for our light sensor, we measure 35kOhm for full brightness, and 3.5 kOhm for full darkness. 35 * 3.5 = 122.5 kOhm. The square root is: 11.068 kOhm. In our resistor box we have resistors of 10kOhm and 15kOhm. We choose the 10kOhm resistor for R.

![](/img/measuring_resistance.jpg)

In order to connect it to a MiniBee, we need to connect to one of the analog inputs of the MiniBee, i.e. A0, A1, A2, A3, A6 or A7.

For this, we can make use of one of the expansion boards of the MiniBee, the [XPree](xpree), or [XPee](xpee).


## With the XPree board

So we first need to solder a header to the expansion board, and then, with the XPree board, we can solder headers to the XPree board, to mount it on a breadboard, and then put it on a breadboard, and make the connections to the light sensor:

![](/img/lightsensor_xpree_01.jpg)
![](/img/lightsensor_xpree_02.jpg)
![](/img/lightsensor_xpree_03.jpg)
![](/img/lightsensor_xpree_04.jpg)
![](/img/lightsensor_xpree_05.jpg)
![](/img/lightsensor_xpree_06.jpg)
![](/img/lightsensor_xpree_07.jpg)

## With the XPee board

On the XPee board, it is easy to connect the resistor and the light sensor:

![](/img/lightsensor_xpee_01.jpg)
![](/img/lightsensor_xpee_02.jpg)
![](/img/lightsensor_xpee_03.jpg)
![](/img/lightsensor_xpee_04.jpg)

# Configuration file

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
