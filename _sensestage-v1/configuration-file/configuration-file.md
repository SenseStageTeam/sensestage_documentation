---
title: Configuration file
summary: An overview of configuration file that the communication software uses
layout: reference
type: reference
guidestep: 0
featured-image: 

creation-date: 2017-02-06
category: software
subcategory: configuration

tags:
    - configuration
related:
    - Connecting a MiniBee for the first time
    - Basic features of the firmware
    - Assigning a MiniBee Configuration via OSC

status: complete
---

The configuration files for PydonHive use the [XML format](https://www.w3schools.com/xml/default.asp).

[Example configurations](https://github.com/sensestage/ssdn_python/blob/master/examples/configuration/) are given in the xml files you find in the `examples/configuration` folder of the package:

The file starts with:

    <xml>
    <hive name="myprojectname">

and ends with:

    </hive>
    </xml>

In between you will define `<minibee />` elements and `<configuration />` elements.

# XML elements

Each XML element is enclosed in `<` and `>`. If an element has child elements, then you have a beginning element: `<element>` and a closing `</element>`. In between you then find other elements. If there are no child elements, you can close the element directly: `<element />` is equivalent to `<element> </element>`.

# Comments

Comments in XML start with `<!--` and end with `-->`. What is in between is ignored by the software that reads the XML, but can be useful for the human that reads the XML.

