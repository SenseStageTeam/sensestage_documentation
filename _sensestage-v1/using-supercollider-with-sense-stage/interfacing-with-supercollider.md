---
title: Using SuperCollider with Sense/Stage
summary: This page describes how to get Sense/Stage data into SuperCollider

layout: guide
type: guide
guidestep: 0
featured-image: 

creation-date: 2017-02-06
category: software
subcategory: examples
tags:
    - todo
related:
    Assigning a MiniBee Configuration via OSC
    OSC interface

---

# The files used in this guide, where to get them

# To include in the guide

* screenshots
* walk-through of what happens


# Starting pydongui from SuperCollider

You can start pydongui.py from SuperCollider with:

```
"pydongui.py".runInTerminal;
// or without opening a terminal window
"pydongui.py".unixCmd;
```

You may also want to start it from your project's directory, so you remember which settings you had for that project (the file needs to be saved for `resolveRelative` to work).

```
(
~mypath = "".resolveRelative;
("cd"+~mypath ++ "; pydongui.py").runInTerminal;
);
```

Then, to ensure that you set the port correctly in pydongui, you can use:

```
// check SC's osc port to ensure where to send the data to:
NetAddr.langPort;

```

For the remainder of this tutorial, set the path to the example configuration XML file as configuration file. After setting the settings, press the [START] button in pydongui.py

# Receiving data

The main OSC messages that will be received are: `/minibee/info`, `/minibee/status` and `/minibee/data`. So we set up some OSC functions to print out these messages. In this example we use `OSCdef`, but you can also use `OSCFunc`.

```
// setup osc receivers (you can also use OSCFunc)
OSCdef( \minibeedata, { |data,time,source| data.postln; }, '/minibee/data' );
OSCdef( \minibeeinfo, { |data,time,src| data.postln; }, '/minibee/info' );
OSCdef( \minibeestatus, { |data,time,src| data.postln; }, '/minibee/status' );

```

For a general guide on using OSC in SuperCollider see:

```
"OSC Communication".openHelpFile;
```

# Assign a configuration via OSC

Now we turn a MiniBee on and after a while we see in the post window of SuperCollider:

```
[ /minibee/info, 0013A20040D75A5B, 1, 0, 0 ]
```

This means that a minibee with serial number 0013A20040D75A5B has connected, and that its ID is 1. And that there are 0 inputs and 0 outputs defined.
This message will keep being sent, as long as the minibee is not configured.
In the post window of `pydongui`, there will be a message that a file has been created and can be edited.
Instead of doing that, you can however send a message to pydongui via OSC like this:

We create a `NetAddr` to send a message to:
```
n = NetAddr.new( "127.0.0.1" , 57600 );
// 57600 is the default port number that pydongui is listening on
// this is the second argument to NetAddr.
```

And then we send a message to assign a configuration to MiniBee number 1:

```
n.sendMsg( "/minibee/configuration", 1, 1 ); // minibee id, config id
```

We use configuration number 1, which enables the accelerometer on board of the MiniBee.

After a while, you will see these messages in the SuperCollider post window:

```
[ /minibee/status, 1, waiting ] // waiting for configuration
[ /minibee/info, 0013A20040D75A5B, 1, 3, 0 ] // three inputs!
[ /minibee/status, 1, configured ] // configured
[ /minibee/status, 1, receiving ] // receiving data
// and a data message!
[ /minibee/data, 1, 0.49114882946014, 0.50030523538589, 0.52911734580994 ]
```

The data message will repeat often!

We can now save this configuration for later use:
```
n.sendMsg( "/minihive/configuration/save", "myfirstconfig.xml");
```


The file will be saved to the directory we started pydongui.py from. So for example:
```
( ~mypath +/+ "*.xml" ).pathMatch;
```
will show the automatically created config, and our `myfirstconfig.xml`

The next time we start up `pydongui` we can choose this configuration file, and the MiniBee will be automatically configured.



# Receiving data

Now that we are receiving data, we can do something useful with the data by adapting
```
OSCdef( \minibeedata, { |data,time,source| data.postln; }, '/minibee/data' );
```

## Routing per MiniBee

The first thing is to separate the data per MiniBee, especially when you use more than one! For this you can use the argument template of `OSCFunc` or `OSCdef`. So to make two different functions for MiniBee id 1 and id 2:

```
(
OSCdef( \minibee1,
    { |data,time,source| "bee 1: ".post; data.postln; },
    '/minibee/data',
    argTemplate: [1]
);
OSCdef( \minibee2,
    { |data,time,source| "bee 2: ".post; data.postln; },
    '/minibee/data',
    argTemplate: [2]
);
);

```

## Viewing the data

The responders above will print out the data to the post window.

To look at the data in a graph, we can use the class `SWPlotterMonitor`, this class is part of the SenseWorld quark.

Firs we set up the OSC function to put the data in a variable we can use elsewhere in the code:
```
(
OSCdef( \minibee1,
    { |data,time,source| ~minibee1data = data.copyToEnd(2); },
    '/minibee/data',
    argTemplate: [1] );
);
```

As the first two items of the data are: `[ /minibee/data, 1, ]`, we just want the data after the second index assigned to our variable.

Then we create the monitor:
```
m = SWPlotterMonitor.new( { ~minibee1data}, 200, 3, 0.005, 10 );

```
The arguments are:

* function that returns data
* number of points to plot
* number of channels (in our case 3)
* delta time for evaluating the function (this is roughly how often data arrives)
* update the plot every N points (slow down the graphics a bit to save CPU)

And then we can start the display:
```
m.start; // start the plot
```

With the key `s` the view will change between superposing the three lines and making a graph for each.

**add screenshots**


To stop watching the data we can do:

```
m.stop; // stop the plot
```

## Example of using the data to control a synth

* use the values in an example

# Sending data

* send PWM data to an LED w/ `/minibee/output`
* example of sending data (control the output rate!)
