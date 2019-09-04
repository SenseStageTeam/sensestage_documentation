---
title: Using the incoming data
summary: This page describes how to get Sense/Stage data into SuperCollider

layout: guide
type: guide
guidestep: 4
parent: Using SuperCollider with Sense/Stage
featured-image:
level: intermediate
priority: 5

creation-date: 2019-09-04
category: software
subcategory: examples
tags:
    - todo
related:
    Assigning a MiniBee Configuration via OSC
    OSC Message Reference
status: fixmesoon
---


Now that we are receiving data, we can do something useful with the data by adapting the `OSCdef`:

```
OSCdef( \minibeedata, { |data,time,source| data.postln; }, '/minibee/data' );
```

# Routing per MiniBee

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

# Viewing the data

The responders above will print out the data to the post window.

To look at the data in a graph, we can use the class `SWPlotterMonitor`, this class is part of the `SenseWorld` quark.

Firs we set up the OSC function to put the data in a variable we can use elsewhere in the code:

```
(
OSCdef( \minibee1,
    { |data,time,source| 
        ~minibee1data = data.copyToEnd(2);
    },
    '/minibee/data',
    argTemplate: [1] );
);
```

As the first two items of the data are: `[ /minibee/data, 1, ]`, we just want the data after the second index assigned to our variable.

Then we create the monitor:
```
m = SWPlotterMonitor.new( { ~minibee1data }, 200, 3, 0.005, 10 );

```
The arguments are:

* a Function that returns data
* number of points to plot
* number of channels (in our case 3)
* delta time for evaluating the function (this is roughly how often data arrives)
* update the plot every N points (slow down the graphics a bit to save CPU)

And then we can start the display:

```
m.start; // start the plot
```

With the key `s` the view will change between superposing the three lines and making a graph for each.

<!-- **add screenshots** -->

To stop watching the data we can do:

```
m.stop; // stop the plot
```



# Simple example of using the data to control a synth

To start using the data to control sound we must first boot the server:

```
s.boot; // boot server
```

And we want as little latency as possible, so we set the server latency to a very low number:
```
s.latency_(0.001);
```

We create a simple three tone sine oscillator:

```
Ndef( \sines, { 
    SinOsc.ar( 
        \freq.kr( [1,1,1], 0.1 ) * 300, // an array argument with 3 values
        0, 
        \amp.kr([0,0,0], 0.1) 
    ).sum 
} );
```

and play it:

```
Ndef( \sines ).play;
```

And then we map the data from MiniBee 1 to it:

```
(
OSCdef( \minibee1,
    { |msg,time,source| 
        var data = msg.copyToEnd(2);
        ~minibee1data = data;
		Ndef( \sines ).setn( \freq, data * 2 * [1,2,3] );
		Ndef( \sines ).setn( \amp, (data - 0.5).abs * 5 );        
    },
    '/minibee/data',
    argTemplate: [1] );
);
```

To look at the sound, we scope it:
```
Ndef( \sines ).scope
```

And if we're fed up with it, we stop the sound again:
```
Ndef( \sines ).stop;
```

Another example, using the `ControlSpec` that is available in SuperCollider:

```
// single sinetone
Ndef( \sines, { SinOsc.ar( \freq.kr( 300, 0.1 ), 0, \amp.kr(0.1, 0.1) ) } );
(
OSCdef( \minibee1, 
	{ |msg,time,source| 
        var data = msg.copyToEnd(2);
        ~minibee1data = data;
		Ndef( \sines ).set( \freq, ([300, 5000, \exp].asSpec.map( data[0] )) );
		Ndef( \sines ).set( \amp, (data[2] - 0.5).abs * 5 );
	};
}, '/minibee/data',
    argTemplate: [1] );
);
Ndef( \sines ).play;
```

And also using a `ControlSpec` for the range of the accelerometer:

```
// specs for mapping:
~accMap = [0.44,0.56].asSpec; // range of accelerometer
~freqMap = [300, 5000, \exp].asSpec; // range of frequency
(
OSCdef( \minibee1,
    { |msg,time,source| 
        var data = msg.copyToEnd(2);
		// using the method .specMap from SenseWorld quark
		Ndef( \sines ).set( \freq, data[0].specMap( ~accMap, ~freqMap ) );
		Ndef( \sines ).set( \amp, (data[2] - 0.5).abs * 5 );
	},
    '/minibee/data',
    argTemplate: [1] );
);
```

To stop the sound:
```
Ndef( \sines ).stop;
```
