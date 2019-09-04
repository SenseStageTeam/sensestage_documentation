---
title: Using SuperCollider with Sense/Stage
summary: This page describes how to get Sense/Stage data into SuperCollider

layout: guide
type: guide
guidestep: 0
featured-image:
level: intermediate
priority: 5

creation-date: 2017-02-06
category: software
subcategory: examples
tags:
    - todo
related:
    Assigning a MiniBee Configuration via OSC
    OSC interface

---

In this tutorial we will show how to receive the data from the MiniBees and how to send data to the MiniBees. And there are some useful extra's like, how to start pydongui from within SuperCollider, and how to do the first configuration with the help of SuperCollider.


# Needed Quarks

In some parts of the tutorial we make use of the tools that are in the Quark `SenseWorld`. Also the Quark `JITLibExtensions` may be of use. You can install them via `Quarks.gui` in SuperCollider, or with code in SuperCollider:

```
Quarks.updateDirectory;

Quarks.install( "SenseWorld" );
Quarks.install( "JITLibExtensions" );

// recompile the language: cmd+shift+l / ctrl+shift+l
thisProcess.recompile;
```
