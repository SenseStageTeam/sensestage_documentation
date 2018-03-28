---
title: Receiving custom data
summary: How to receive custom data with the firwmare
layout: documentation
type: guide
parent: Customizing firmware
guidestep: 2
creation-date: 2018-03-28
tags: 
    - expert
category: firmware
subcategory: minibee
---

## Receiving custom data

You can also send wireless data to the MiniBee and perform a custom action with it. For this, you need to again define some custom pins (assuming you use some custom output for this), and define a callback function which is called whenever a custom message is sent to the MiniBee. For this you define a separate function (so not inside the `setup()` or `loop()` functions!):

```
void customMsgParser( char * msg ){

// this will be our parser for the custom messages we will send:
// msg[0] and msg[1] will be node ID and message ID
// the remainder are the actual contents of the message
// if you want to send several kinds of messages, you can e.g.
// switch based on msg[2] for message type
     if ( msg[2] > 0 ){ // change speed yes/no
       stepper.setSpeed( msg[3] ); // third argument of message is the speed
     }
     if ( msg[4] == 0 ) // third argument is the direction
       stepper.step( -1 * msg[5] ); // fifth argument is the amount of steps to do
     else
       stepper.step( msg[5] ); // fifth argument is the amount of steps to do
}
``` 

In the `setup()` function you then add:
  
```
  // set the custom message function
  Bee.setCustomCall( &customMsgParser );
```

See the &#8220;MiniBee/customReceiving&#8221;-example for a full example.

The message you need to send to the MiniBees is formatted as follows:

  * &#8216;E&#8217; &#8211; single character, indicating the custom message type
  * node ID &#8211; this is the identifier of the MiniBee we are targeting
  * message ID &#8211; this is an unique number for each message, in order to prevent the firmware from reacting twice to the same message
  * data &#8211; any number of bytes of data. These will be passed onto the callback function in the msg-bytes from index 2 and higher.

You can send an OSC message `/minibee/custom` from your software and to send the data to the MiniBee.

## TODO

- expand on this a bit