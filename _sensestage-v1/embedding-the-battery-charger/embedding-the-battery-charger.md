---
title: Embedding the battery charger
summary: How to embed your battery charger into your Minibees, so that you can charge the battery without removing it from your system.

layout: guide
type: guide
guidestep: 0
featured-image:

level: basics
priority: 10

permalink: /sensestage-v1/embedding-the-battery-charger/

creation-date: 2018-02-06
category: hardware
subcategory: battery
---

In some cases you may want to embed the battery charger in your setup, rather than having to unplug the battery each time you want to charge it. With a little bit of soldering, this is entirely feasible to do!

# Connecting a wire to the battery charger

If you look at the battery charger, you notice two holes in the middle of the board, marked `+` and `-`.

![](/img/usb-battery-charger.jpg)

To this you can connect a [JST Jumper wire](https://www.sparkfun.com/products/8670):

![](/img/jst_jumper_wire.jpg)

The red wire is soldered to the `+` and the black wire to the `-`.

You can then connect your battery to the charger and plug in the cable you soldered to the MiniBee.

## Alternative: solder to the MiniBee

If you don't have a JST jumper wire available, you can solder two wires (I recommend using red for `+` and black for `-`) between the charger board and the MiniBee.

In revision F we added pads at the bottom of the MiniBee to solder a power connection to:

![](/img/minibee_revF_bottom_annotated.png)

For revision D it is a bit more complicated, you can solder to the JST connector:

![](/img/minibee_bare_plus-minus.png)

or use the pads at the bottom for the coin cell (blue in the image):

![](/img/minibee_annotated-D-back-plus-minus.png)
