---
title: Receiving and sending custom data
summary:
layout: reference
type: reference
guidestep: 3
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

The MiniBee firmware gives the possibility to add custom data exchange between the user software and the MiniBee. Custom sensor data (added with the function `addCustomData`) is just received along with the other sensor data with the `/minibee/data` message.

But in some cases you may want to send other data, e.g. in reply to a custom message that you sent to the MiniBee (with `/minibee/custom`) to confirm that it has been received. For this `/minibee/private` may be used.

`/minibee/trigger` can be sent from the MiniBee to send time critical data; e.g. you may check for changes in digital pins and send upon change, while the general sensor data is sent out less frequently.


```
    /minibee/custom - iii..i
```
*from user software to MiniBee*

* `i` - the ID of the MiniBee
* `ii..i` - as many integer values as you have defined in your custom firmware. You have to make sure in your user software that the integer values that you send are in the range of 0 to 255.

Also, make sure that the values you send correspond to how you interpret the data in the `customMsgParser`-function in your custom firmware.


```
    /minibee/private   - iff..f
```
*from MiniBee to user software*

* `i` - the ID of the MiniBee
* `ff..f` - a number of floating point data values that correspond to the sensors that are attached. The order of these values is always:

```
    /minibee/trigger   - iff..f
````
*from MiniBee to user software*

* `i` - the ID of the MiniBee
* `ff..f` - a number of floating point data values that correspond to the sensors that are attached. The order of these values is always:
