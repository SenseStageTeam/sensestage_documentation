---
title: Hardcoded configuration
summary: Hardcoding the configuration in the firmware
layout: guide
type: guide
parent: Customizing firmware
guidestep: 5
creation-date: 2018-03-28
tags:
    - expert
category: firmware
subcategory: minibee
---


In some cases you may not want to have a flexible configuration, but instead fix the configuration in the firmware, for example if you are using the boards to communicate between each other, rather than with a central host, or if you have a busy network and don't want the startup communication for the configuration to happen.

For this purpose the methods `setRemoteConfig` and `readConfigMsg` are there:

- `setRemoteConfig` sets the level of remote configuration:
    - *0* no remote config and no remote configuration of the id of the XBee: in this case you need to [configure the `MY` address of the XBee manually](using-x-ctu-to-change-settings-of-an-xbee).
    - *1* no remote config, but id of the XBee is remotely set.
    - *2* remote configuration for both id and configuration of pins.
- `readConfigMsg` reads an array in as a configuration for the MiniBee, see the example below:

Outside of any functions:

```
/// we use a fixed configuration for the MiniBee, rather than use a remote wireless configuration
/// Here we define:
/// pins D3, D5, D6, D9, D10, D11 as analog outputs
/// pin D7 as digital input
/// pin D8 as digital output
/// pins A0, A1, A2 as analog inputs
/// and we use the onboard ADXL accelerometer via the TwoWire interface
uint8_t myConfig[] = { 0, 1, 0, 50, 1, // null, config id, msgInt high byte, msgInt low byte, samples per message
  AnalogOut, NotUsed, AnalogOut, AnalogOut, DigitalIn, DigitalOut, // D3 to D8 (D4 is reserved for status LED)
  AnalogOut, AnalogOut, AnalogOut, NotUsed, NotUsed,  // D9,D10,D11,D12,D13 (D12, D13 are also reserved)
  AnalogIn10bit, AnalogIn10bit, AnalogIn10bit, NotUsed, TWIData, TWIClock, NotUsed, NotUsed, // A0, A1, A2, A3, A4, A5, A6, A7
  1, TWI_ADXL345 // 1 I2C/TWI device: the ADXL
};
```

Inside the `setup()` function:

```
  // just listening
  Bee.setRemoteConfig( 0 );
   /// arguments are the baudrate, and the board revision
  Bee.setup(57600, 'D' );
  Bee.readConfigMsg( myConfig, 26 ); // second argument is the size in bytes of the myConfig array
```

For a full example, see the [`BeeToBee` example](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn/examples/BeeToBee)
