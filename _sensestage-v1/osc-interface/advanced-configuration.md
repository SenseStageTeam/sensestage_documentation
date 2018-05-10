---
title: Advanced configuration
summary: 
layout: reference
type: reference
guidestep: 6
featured-image: 
parent: OSC interface

creation-date: 2017-02-06
category: software
subcategory: interfaces

tags:
    - osc
    - interface
    - communication

---

It is also possible to create completely new configuration elements via OSC. After you have created a configuration element, you can save the configuration file or assign the configuration element to an unconfigured MiniBee.


```
    /minihive/configuration/create isiiii...
```

*From user software to communication software*
    
Format:

* `i`: configuration ID
* `s`: configuration name
* `i`: samples per message
* `i`: message interval
* `i`: number of pins defined (N)
* `i`: number of TWI devices defined (M)

* then N times:
  * `s`: pin id (e.g. A0)
  * `s` or `i`: pin function (e.g. 3, or 'AnalogIn')
  * `s`: pin label (e.g. light)

* then M times:
  * `i`: twi id (e.g. 0)
  * `s` or `i`: twi function (e.g. 10, or 'ADXL345')
  * `s`: twi label (e.g. accelero)

```
    /minihive/configuration/short isiiii
```

*From user software to communication software*

as above but without separate pin definitions; those are done separately by the message that follow.

* `i`: configuration ID
* `s`: configuration name
* `i`: samples per message
* `i`: message interval
* `i`: number of pins defined (N)
* `i`: number of TWI devices defined (M)

```
    /minihive/configuration/pin iis / iii
```

*From user software to communication software*

Configuration per pin

* `i`: configuration ID
* `s`: pin id (e.g. A0)
* `s` or `i`: pin function (e.g. 3, or 'AnalogIn')

```
    /minihive/configuration/twi iii / iis
```

*From user software to communication software*

Configuration per twi device

* `i`: configuration ID
* `i`: twi id (e.g. 0)
* `s` or `i`: twi function (e.g. 10, or 'ADXL345')

```
    /minihive/configuration/query i 
```

*From user software to communication software*

* `i` configuration ID


```
    /minihive/configuration/pin/query is
```

*From user software to communication software*

* `i`: configuration ID
* `s`: pin id (e.g. A0)


```
    /minihive/configuration/twi/query ii
```

*From user software to communication software*

* `i`: configuration ID
* `i`: twi id (e.g. 0)


```
    /minihive/configuration/delete i
```

*From user software to communication software*

* `i` configuration ID

possible return messages are:

```
    /minihive/configuration/error i
    /minihive/configuration/delete/done i
```

* `i` configuration ID
