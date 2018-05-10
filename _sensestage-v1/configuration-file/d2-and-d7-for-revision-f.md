---
title: D2 and D7 for revision F
summary: An overview of configuration file that the communication software uses
layout: reference
type: reference
guidestep: 3
parent: Configuration file
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

With board revision F, the connection of pin D2 to the XBee sleep pin was changed: instead pin D7 is connected to the XBee sleep pin, and pin D2 is connected to the pin header instead of D7. In order to keep backwards compatibility of expansion boards the firmware and software behave as follows:

* if pin `D2` is defined in the configuration file, then the function defined there is used
* if pin `D7` is defined in the configuration file, and no function is defined for `D2`, then the function defined for `D7` is used for pin `D2`.
* if both `D2` and `D7` are defined in the configuration file, then the function defined for `D2` is used for the pin, and the function for `D7` is ignored.
* For older minibee revisions any configuration of pin `D2` is ignored.

For revision F the software performs a check to move the configuration of pin `D2` to `D7`.
