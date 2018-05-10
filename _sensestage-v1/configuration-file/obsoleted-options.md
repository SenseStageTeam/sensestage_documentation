---
title: Obsoleted options
summary: An overview of configuration file that the communication software uses
layout: reference
type: reference
guidestep: 5
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

# Pin options from configurations for [older versions of the firmware](basic-features-of-the-firmware#obsolete) {#oldoptions}

As of firmware version 10, the Ping and SHT are no longer supported standard in the firmware. They are supported in firmware versions up to 8.

* `Ping` — Ultrasonic sensor (any pin *except* for A4, A5, A6, A7)
* `SHTClock` — Clock signal for SHT15 sensor (temperature/humidity) (any pin *except* for A4, A5, A6, A7)
* `SHTData` — Data signal for SHT15 sensor (temperature/humidity) (any pin *except* for A4, A5, A6, A7)

# TWI options

In firmware version up to 8, the following other TWI devices were supported: `LIS302DL`, `TMP102`, `BMP085` and `HMC58X3`.

An example with multiple TWI devices:

    <configuration id="2" name="environment" message_interval="50" samples_per_message="1" redundancy="3">
        <twi id="1" device="ADXL345" name="accelero"/>
        <twi id="2" device="TMP102" name="tmp" />
        <twi id="3" device="BMP085" name="bmp"/>
    </configuration>
