---
title: Power supply
summary: Power supply options for the MiniBee.
layout: documentation
type: guide
creation-date: 2017-02-06
category: hardware
subcategory: battery
tags:
    - todo
---

* How long do batteries last?
* How do power my MiniBee with a different kind of battery?
* Or from a wall plug?

* What kind of power does the MiniBee supply me with?


The Sense/Stage MiniBee runs at 3.3 V. On board there is a power regulator, which can regulate power from 3.3 V to 5V down to a steady 3.3 V.

Thus the ideal choice for a battery is one that outputs 3.6 or 3.7 V. We have tested a few of these batteries, the results of these tests can be found here.

The batteries can also be used to power a couple of sensors that are attached to the MiniBee. For this purpose, the 3.3 V output is supplied in the header.

If you want to power something that needs a higher voltage, you can either use a power step-up circuit, or use a wallwart power supply. In this case, it will be wise to use another power regulator (e.g. a 7805) to supply the power to the MiniBee (but still use the battery connector).

There is a fuse on the Sense/Stage MiniBee, which will shut it down if you shortcircuit it accidentally.



# TODO

- rewrite this page
