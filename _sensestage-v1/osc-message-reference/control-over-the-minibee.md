---
title: Control over the MiniBee
summary:
layout: reference
type: reference
guidestep: 6
featured-image:
parent: OSC Message Reference

creation-date: 2017-02-06
category: software
subcategory: interfaces

tags:
    - osc
    - interface
    - communication

status: complete
---

There are some options to control the behaviour of the MiniBee:

* you can pause and unpause a MiniBee with `/minibee/run` (make it temporarily stop sending data and resume again)
* debug the behaviour by enabling a loopback: `/minibee/loopback`
* re-initialize the minibee firmware with `/minibee/announce`
* reset the minibee with `/minibee/reset`
* reset all minibees with `/minihive/reset`
* save the node id (on the XBee) with `/minibee/saveid`
* save the node id for all XBees with `/minihive/ids/save`




```
    /minibee/run - ii
```
*Running / pausing a minibee*.

* `i` - the minibee id
* `i` - whether to pause (0) or run (1) the minibee

This feature is useful if you want to save bandwidth in a network with a lot of MiniBees.

```
    /minibee/loopback - ii
```

Getting a *loopback* message sent back from the minibee, i.e. a copy of each message sent to the minibee. This is useful for debugging.


* `i` - the minibee id
* `i` - 0 (for not sending messages back) or 1 (for sending each message back)

```
    /minibee/announce - i
```

*Re-initialize the MiniBee firmware*

If you want to re-initialize the firmware (without resetting it), you can send a message to do so. This can be useful if a MiniBee was already on, when you started the software.

* `i` - the minibee id


```
    /minibee/reset - i
```

*Reset a MiniBee.*

This will reset the Atmega328 chip, so effectively restart the firmware. This can be useful if for some reason the MiniBee got stuck.


* `i` - the minibee id


```
    /minihive/reset
```
*To reset all minibees*


```
    /minibee/saveid - i
```

*Save the ID of the XBee*. By default the XBees have an ID of 0xFFFA. During the configuration process the ID is set to the number defined in the configuration file. If you want to save this ID to the MiniBee, this step will not be necessary in the configuration process, and the startup procedure may go a little bit faster.

* `i` - the minibee id

```
    /minihive/ids/save
```

To save the IDs on all minibees that are turned on:
