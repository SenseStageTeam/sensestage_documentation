---
title: Sending custom data
summary: How to send custom data from the firwmare
layout: documentation
type: guide
parent: Customizing firmware
guidestep: 1
creation-date: 2018-03-28
tags: 
    - expert
category: firmware
subcategory: minibee
---

If you want to send custom data from the MiniBee, you have to:

- define the customized pins and/or amount and size of the custom data in the `setup()` function
- add your [custom data to the data packet](#adddata) in the `loop()` function
- [upload the customized firmware to your MiniBee](uploading-firmware-to-a-minibee)
- adapt the [configuration file](#adaptconfig)


## Defining a customized pin

A pin can be defined in the firmware to have a custom definition. In that case, the pin cannot be assigned another functionality through the wireless configuration.

In the firmware you use the method `setCustomPin` in the `setup()` function:

```
Bee.setCustomPin( 10, 0 );
Bee.setCustomPin( 14, 2 );
Bee.setCustomPin( 15, 2 );
```

The first argument is the number of the pin (3 to 13 for the digital ones, 14 to 21 for the analog pins), the second argument indicates how many bytes of data the pin will provide.

- For an output pin (controlling something from the board) this will be 0.
- For an input pin this will be 1, 2, 3 or 4.

You then have to take care yourself to initialise the pins properly as is usually done in Arduino code, by setting their `pinModes`.

```
pinMode( 10, OUTPUT );
pinMode( 14, INPUT );
pinMode( 15, INPUT );
```

### Defining multiple customized pins

In case you want to define multiple customized pins at once you can use `setCustomPins` (in the `setup()` function):

```
uint8_t cpins []  = {10,14,15 };
uint8_t csizes [] = { 0, 2, 2 };
Bee.setCustomPins( cpins, csizes, 3 );
```


## Defining an arbitrary custom input

If you generate data you want to send over based on something that is not associated with a pin, you have to set the size of the data in advance with the method `setCustomInput`. This method has two arguments: the number of inputs and the size (in bytes) of each of these inputs.

For 3 inputs of 2 bytes:

```
Bee.setCustomInput( 3, 2 );
```

If you have different size inputs, you can set it multiple times, e.g for 3 inputs of 2 bytes and 4 of 1 byte:


```
Bee.setCustomInput( 3, 2 );
Bee.setCustomInput( 4, 1 );
```


## Adding your custom data to the package that will be send out: {#adddata}

In the `loop()` function you have to add the data you created by calling the function `addCustomData` before the `doLoopStep()` function. The first argument of `addCustomData` is an array containing the data that needs to be added; the second argument is the size of this array:

```
int myData[2];
myData[0] = analogRead( 14 );
myData[1] = analogRead( 15 );
// add our customly measured data to the data package:
Bee.addCustomData( myData, 2 );
// do a loop step of the remaining firmware:
Bee.doLoopStep();
```

Again: `addCustomData` can be called multiple times if you have data from different sizes:

```
int myData[3];
myData[0] = analogRead( 14 );
myData[1] = analogRead( 15 );
myData[2] = analogRead( 16 );


char myOtherData[4];
myOtherData[0] = 1;
myOtherData[1] = 32;
myOtherData[2] = 64;
myOtherData[3] = 127;

// add our customly measured data to the data package:
Bee.addCustomData( myData, 3 );
Bee.addCustomData( myOtherData, 4 );
// do a loop step of the remaining firmware:
Bee.doLoopStep();
```


## Adjusting the configuration file for the custom data {#adaptconfig}

When the MiniBee sets up the communication with the Hive software, it will report how many custom inputs it has. To parse the data properly, you need to add information in the configuration file to indicate what additional data will be coming in. This can be done in two possible places:

- in the `<minibee>` element, inside `<custom>` ... `</custom>` tags.
- in the `<configuration>` element, inside `<customconf>` ... `</customconf>` tags.

If you use the same custom configuration for multiple minibees, you probably want to put the definition inside the `<configuration>` element. If it is really just the one MiniBee that will use this customization, you can put it inside the `<minibee>` element.

Then for each data point you create an element `<data>` like: `<data id="1" size="1" offset="0" scale="255" name="ldr1"/>`

- `id` - is the order in the data
- `size` - the size in bytes
- `offset` - the offset in the data
- `scale` - the scaling factor of the data

The data that is sent out via OSC is calculated from `offset` and `scale` with the formula: `(data_in_bytes - offset)/scale`. So by defining the offset and scale in the configuration file, you can scale the data sent via OSC to floating point between 0 and 1 or -1 and 1.

**Examples:**

```
<minibee id="1" revision="F" serial="0013A2004049875B" libversion="8" caps="0" configuration="1">
  <custom>
	<data id="0" size="2" offset="0" scale="1024" name="amp"/>
	<data id="1" size="2" offset="0" scale="1024" name="ldr1"/>
  </custom>
</minibee>
```

```
<configuration id="3" message_interval="15" name="lsm" redundancy="3" rssi="False" samples_per_message="1">
  <pin config="TWIClock" id="A5" name="None"/>
  <pin config="TWIData" id="A4" name="None"/>
  <twi device="ADXL345" id="1" name="accelero"/>
  <customconf>
	<data id="0" size="2" offset="0" scale="1024" name="amp"/>
	<data id="1" size="2" offset="0" scale="1024" name="ldr1"/>
	<data id="2" size="2" offset="0" scale="1024" name="ldr2"/>
	<data id="3" size="1" offset="0" scale="1" name="otherdata-one"/>
	<data id="4" size="1" offset="0" scale="64" name="otherdata-two"/>
	<data id="5" size="1" offset="0" scale="128" name="otherdata-three"/>
	<data id="6" size="1" offset="0" scale="256" name="otherdata-four"/>
  </customconf>
</configuration>
```    

## Example - sending data from capacitive sensors:

This is the [customSending](https://github.com/sensestage/ssdn_minibee/tree/master/libraries/MiniBee_APIn/examples/customSending)-example for a full example which used an older version of the [Capacitive Sensing library for Arduino](https://playground.arduino.cc/Main/CapacitiveSensor?from=Main.CapSense)

```
/// Wire needs to be included if TWI is enabled
#include <Wire.h>
#include <ADXL345.h>

/// includes needed in all cases
#include <XBee.h>
#include <MiniBee_APIn.h>

/// in our example we are using the capacitive sensing library to use sensors
/// not supported by default in our library
#include <CapSense.h>

MiniBee_API Bee = MiniBee_API();

/// using pin 11 as send pin, and pins 8, 9 and 10 as sensing pins
/// mount a 10M resistor between each of the sensing pins and 11, so between pin 8 and 11, between pin 9 and 11 and between 10 and 11.
 // at each add a wire and or foil which becomes your capacitive sensor
 CapSense   cs_11_10 = CapSense(11,10);       
 CapSense   cs_11_9  = CapSense(11,9); 
 CapSense   cs_11_8  = CapSense(11,8); 

/// variables for sensing our data
int capData[3];
long total[3];

void setup() {
  Bee.setup(57600,'D');

  // define which pins we will be using for our custom functionality:
  // arguments are: pin number, size of data they will produce (in bytes)
  /// in our case we use pin 10 (no data)
  /// and pins 8, 9, and 10, each 2 bytes, as we are going to send integers
  Bee.setCustomPin( 11, 0 );
  Bee.setCustomPin( 10, 2);
  Bee.setCustomPin( 9, 2 );
  Bee.setCustomPin( 8, 2 );
  
  // if you generate data without a pin associated, use setCustomInput
  //   Bee.setCustomInput( 1, 1 ); //uint8_t noInputs, uint8_t size );
}

void loop() {
  /// do our measurements
  total[0] =  cs_11_10.capSense(30);
  total[1] =  cs_11_9.capSense(30);
  total[2] =  cs_11_8.capSense(30);

  for ( uint8_t j=0; j<3; j++ ){
    capData[j] = (int) total[j];
  }
  // add our customly measured data to the data package:
  Bee.addCustomData( capData, 3 ); // arguments: reference to the data array and size of the array (3))
  // do a loop step of the remaining firmware:
  Bee.loopStep();
}
```

And our configuration element in the config file becomes (assuming different sensitivities and offsets for our actual sensors):

```
<configuration id="3" message_interval="15" name="capsense" redundancy="3" rssi="False" samples_per_message="1">
  <customconf>
	<data id="0" size="2" offset="20" scale="1000" name="antenna1"/>
	<data id="1" size="2" offset="40" scale="500" name="touch1"/>
	<data id="2" size="2" offset="40" scale="500" name="touch2"/>
  </customconf>
</configuration>
```
