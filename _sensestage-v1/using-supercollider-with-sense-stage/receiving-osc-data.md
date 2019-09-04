---
title: Receiving OSC data
summary: This page describes how to get Sense/Stage data into SuperCollider

layout: guide
type: guide
guidestep: 2
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

The main OSC messages that will be received from pydon are: `/minibee/info`, `/minibee/status`, `/minibee/rssi` and most important `/minibee/data`. So we set up some OSC functions to print out these messages. In this example we use `OSCdef`, but you can also use `OSCFunc`.

```
// setup osc receivers (you can also use OSCFunc)
OSCdef( \minibeedata, { |data,time,source| data.postln; }, '/minibee/data' );
OSCdef( \minibeerssi, { |data,time,source| data.postln; }, '/minibee/rssi' );
OSCdef( \minibeeinfo, { |data,time,src| data.postln; }, '/minibee/info' );
OSCdef( \minibeestatus, { |data,time,src| data.postln; }, '/minibee/status' );

```

For a general guide on using OSC in SuperCollider see:

```
"OSC Communication".openHelpFile;
```

For an overview of all OSC messages that Pydon sends and understands, see the [OSC message reference](/sensestage-v1/osc-message-reference)
