---
title: Power supply
summary: Power supply options for the MiniBee.
layout: documentation
type: guide
date: 2017-02-06
category: hardware
subcategory: battery
tags:
    - todo
---




The Sense/Stage MiniBee runs at 3.3 V. On board there is a power regulator, which can regulate power from 3.3 V to 5V down to a steady 3.3 V.

Thus the ideal choice for a battery is one that outputs 3.6 or 3.7 V. We have tested a few of these batteries, the results of these tests can be found here.

The batteries can also be used to power a couple of sensors that are attached to the MiniBee. For this purpose, the 3.3 V output is supplied in the header.

If you want to power something that needs a higher voltage, you can either use a power step-up circuit, or use a wallwart power supply. In this case, it will be wise to use another power regulator (e.g. a 7805) to supply the power to the MiniBee (but still use the battery connector).

There is a fuse on the Sense/Stage MiniBee, which will shut it down if you shortcircuit it accidentally.



There is an obvious compromise to be made between battery size and battery capacity, and so we decided to consider two configurations:

* for usage cases where size is not a concern, e.g. when the board is used for fixed environmental sensing, a large, high-capacity battery is best; and
* for situations where size is important (mounted on a performer’s body or a handheld instrument, for example) and the battery should be as small as possible.

For logistical and ecological reasons, the battery should be rechargeable, and last at least as long as one rehearsal, i.e. approximately 5 to 6 hours. Our board draws about 70 mA of current, when used with a regular XBee, transmitting data every 50 ms, without activating a sleep mode.

The batteries we have tested include:

AA-sized Li-Ion 900 mAh
(Protected UltraFire 14500 AA sized 3.6V Li-Ion Rechargeable Battery 900 mAh CR14500)
Long battery life (almost 10 hours).
Recharge time ca 3 hours (with Ultrafire WF-138 3.6 volt Lithium-Ion AA / AAA battery charger from batteryjunction.com).
Usable with a standard AA-battery holder.
Towards the end of the battery life, the battery turns off at intervals of about 10 seconds and turns on again, rather than just turn off completely.

AAA-sized Li-Ion 500 mAh
(UltraFire 10440 AAA Li-Ion 3.6V Rechargeable Battery 500 mAh CR10440, together with “Protection circuit Module (PCB) for 3.6V(3.7V) Li-ion (18650/18500) cell Battery”)
Unfortunately, we found that a majority of these batteries would not recharge after using them only a few times.

18650 Li-Ion 2400 mAh
(Protected UltraFire 18650 3.6V Li-Ion rechargeable Battery 2400 mAh)
Very long battery life (ca. 24 hours).
Recharge time ca. 12 hours.
Large battery, but useful for installations where size is not a constraint and recharging is part of the design, e.g. solar powered recharging.

Li-Poly Sparkfun 860mAh
(Polymer Lithium Ion Batteries – 860mAh; Sparkfun no: PRT-00341)
Long battery life (almost 10 hours).
Recharge time ca. 2.5 hours (Using the LiPoly Fast Charger; SparkFun no: PRT-08293).
Battery is slightly larger than the board, but very flat.

Li-Ion coin cell Sparkfun 200mAh
(Coin Cell Battery Rechargeable – 24.5mm; Sparkfun no: PRT-08818; together with “Protection circuit Module (PCB) for 3.6V(3.7V) Li-ion (18650/18500) cell Battery”)
Short battery life (almost 2 hours).
Recharge time ca. 30 minutes (Using the LiPoly Fast Charger; SparkFun no: PRT-08293).
This coin cell fits within the footprint of the PCB so a battery clip has been added in the revision B of the board.


# TODO

- rewrite this page
