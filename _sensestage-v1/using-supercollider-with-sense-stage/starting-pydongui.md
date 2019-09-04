---
title: Starting PydonGui
summary: This page describes how to get Sense/Stage data into SuperCollider

layout: guide
type: guide
guidestep: 1
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
    OSC interface
status: fixmesoon
---


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

For the remainder of this tutorial, set the path to the example configuration XML file as configuration file. After setting the settings, press the [START] button in pydongui.py.


>> If the configuration works fine, then in the future you can use the autostart function, so you don't need to press the button each time for startup. This is done with the checkbox in the upper right corner of the GUI.

## Using pydoncli instead

Instead of using the pydongui, you can also use pydoncli. Pydoncli is the command line equivalent of pydongui and uses the same .ini file for its settings.

So if you've started the network once with pydongui, and set all the settings, if you then start pydon with the command line variant (from the same directory), it will take the same settings. And in addition you can change parameters from the command line, such as the port to which to send the data. This is useful especially for SuperCollider where sometimes the port where it listens on OSC can be different (e.g. after a crash). If you start pydoncli from SuperCollider in the following way, you ensure that you will always have the right port:


```
(
~mypath = "".resolveRelative;
("cd"+~mypath ++ "; pydoncli.py -t" + NetAddr.langPort).runInTerminal;
);
```

If you want to know what other settings you can set from the command line, type `pydoncli.py -h` in a terminal.
