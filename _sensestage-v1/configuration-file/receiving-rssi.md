---
title: Receiving RSSI
summary: An overview of configuration file that the communication software uses
layout: reference
type: reference
guidestep: 4
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

From version 0.42 onwards, you automatically receive the RSSI data for each MiniBee with the OSC-message `/minibee/rssi`.


From pydon version 0.32 (June 2013) to 0.41 (April 2018) you could define in the configuration element to receive RSSI as a data point in the `/minibee/data` OSC-message.

The old format was:

    <configuration id="2" name="environment" message_interval="50" samples_per_message="1" redundancy="3" rssi="True">
        <pin id="A0" config="AnalogIn" name="light" />
        <twi id="1" device="ADXL345" name="accelero"/>
    </configuration>


- *RSSI* specifies whether or not the RSSI (received signal strength indication) data from the wireless transmission should be transmitted as data. If you want to have this data available it should be set to “True” (case-sensitive).

