---
title: Configuration
summary: 
layout: reference
type: reference
guidestep: 4
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

If a MiniBee is not defined in the configuration file, you can send an OSC message to configure it with a configuration that is defined in the file with the message `/minibee/configuration`.

Aftwards you can send a message to save the configuration file (`/minihive/configuration/save`). You can also load a new configuration file (`/minihive/configuration/load`).



```
    /minibee/configuration - ii(s)
```

*From user software to MiniBee*

* `i` - the ID of the MiniBee
* `i` - the ID of the configuration; this configuration has to be defined in the configuration file
* `s` - (optional) the serial number of the MiniBee

The hive sends a message back to confirm or to indicate an error. The arguments are the same as the message above.

```
    /minibee/configuration/done  - ii(s)
    /minibee/configuration/error - ii(s)
```

You can load and save a configuration file via OSC:

```
    /minihive/configuration/save  - s 
```

*From user software to communication software*

* `s` - the filename to save to


```
    /minihive/configuration/load  - s 
```

*From user software to communication software*


* `s` - the filename to load from

