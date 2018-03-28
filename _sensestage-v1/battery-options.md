---
title: Battery options
summary: Various options to power the minibee
layout: documentation
type: reference
creation-date: 2018-03-28
category: hardware
subcategory: battery
tags:
    - overview

---

There is an obvious compromise to be made between battery size and battery capacity, and so we decided to consider two configurations:

  * for usage cases where size is not a concern, e.g. when the board is used for fixed environmental sensing, a large, high-capacity battery is best; and 
  * for situations where size is important (mounted on a performer's body or a handheld instrument, for example) and the battery should be as small as possible. 

For logistical and ecological reasons, the battery should be rechargeable and last at least as long as one rehearsal, i.e. approximately 5 to 6 hours. Our board draws about 70 mA of current, when used with a regular XBee, transmitting data every 50 ms, without activating a sleep mode. Depending on what sensors you have attached, you may consume more current.

The batteries we have tested include:

## Li-Ion Poly 500 mAh

*Lithium Ion Polymer Battery - 3.7v 500mAh from Floris.cc*

Battery is about as large as, though a bit wider than the board, very flat.

## Li-Poly Sparkfun 400mAh
  
*Polymer Lithium Ion Batteries &#8211; 400mAh; Sparkfun no: PRT-13851*
  
<!-- Long battery life (almost 6 hours). -->
  
<!-- Recharge time ca. 2.5 hours (Using the LiPo Charger Basic; SparkFun no: PRT-10401). -->
  
Battery is about as large as the board, very flat.


## Li-Poly Sparkfun 860mAh
  
*Polymer Lithium Ion Batteries &#8211; 860mAh; Sparkfun no: PRT-00341*

- measurements made with revision A of the MiniBee in 2010

Long battery life (almost 10 hours).
  
Recharge time ca. 2.5 hours (Using the LiPoly Fast Charger; SparkFun no: PRT-08293).
  
Battery is slightly larger than the board, very flat.



## Li-Ion coin cell Sparkfun 200mAh
  
*Coin Cell Battery Rechargeable &#8211; 24.5mm; Sparkfun no: PRT-08818* <br />
together with *Protection circuit Module (PCB) for 3.6V(3.7V) Li-ion (18650/18500) cell Battery*

- measurements made with revision A of the MiniBee in 2010

Short battery life (almost 2 hours).
  
Recharge time ca. 30 minutes using the LiPoly Fast Charger; SparkFun no: PRT-08293.
  
This coin cell fits within the footprint of the PCB so a battery clip has been added from revision B of the board.



## AA-sized Li-Ion 900 mAh
  
*Protected UltraFire 14500 AA sized 3.6V Li-Ion Rechargeable Battery 900 mAh CR14500*

- measurements made with revision A of the MiniBee in 2010
  
Long battery life (almost 10 hours).
  
Recharge time ca 3 hours (with *Ultrafire WF-138 3.6 volt Lithium-Ion AA / AAA battery charger*).
  
Usable with a standard AA-battery holder.
  
Towards the end of the battery life, the battery turns off at intervals of about 10 seconds and turns on again, rather than just turn off completely.


## 18650 Li-Ion 2400 mAh
  
*Protected UltraFire 18650 3.6V Li-Ion rechargeable Battery 2400 mAh*

- measurements made with revision A of the MiniBee in 2010

Very long battery life (ca. 24 hours).
  
Recharge time ca. 12 hours.
  
Large battery, but useful for installations where size is not a constraint and recharging is part of the design, e.g. solar powered recharging.




## AAA-sized Li-Ion 500 mAh
  
*UltraFire 10440 AAA Li-Ion 3.6V Rechargeable Battery 500 mAh CR10440* <br />
together with *Protection circuit Module (PCB) for 3.6V(3.7V) Li-ion (18650/18500) cell Battery*
  
Unfortunately, we found that a majority of these batteries would not recharge after using them only a few times.

>Our advice: don't use batteries that don't come with their own protection circuit built-in.
