---
title: Assign a configuration
summary: This page describes how to get Sense/Stage data into SuperCollider

layout: guide
type: guide
guidestep: 3
parent: Using SuperCollider with Sense/Stage
featured-image:
level: intermediate
priority: 5

creation-date: 2019-09-04
category: software
subcategory: examples
related:
    Assigning a MiniBee Configuration via OSC
    OSC Message Reference
status: done
---

The pydon osc interface allows us to configure new MiniBees with an OSC message. In this tutorial we assume that you use the `example_hiveconfig.xml` that is supplied with the pydon package as the starting configuration file.


After we've set up the `OSCdefs` as described on the previous page, we turn on an unconfigured MiniBee. After a while we see in the post window of SuperCollider:


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
will show the automatically created config, and our `myfirstconfig.xml`.

The next time we start up `pydongui` we can choose this configuration file, and the MiniBee will be automatically configured.
