---
title: Choosing a radio frequency for the XBee
summary: This page describes how to choose a good radio frequency for the XBee.
layout: documentation
type: guide
creation-date: 2017-05-04
tags: 
    - advanced
    - todo
category: hardware
subcategory: xbee
related:
  - Using X-CTU to change settings of an XBee
---

The XBees use the 2.4 GHz range for the wireless communication. This is the same range within which WiFi is communicating and Bluetooth. To avoid clashes between these networks, there are different subbands which can be used, in addition to the different protocol negotiations to accept or reject messages.

In the settings of the XBee, the `channel` (`ATCH`) determines on which radio frequency the XBee is transmitting.

If you have troubles with the XBee communication, then you can change the channel to a subband that is less crowded. This page describes how to do this. If this does not help, then using an external antenna or an XBee Pro can help to get a stronger signal.

# Using spectrum analyzer of X-CTU


First follow the instructions to [get X-CTU](using-x-ctu-to-configure-an-xbee#getting) and [select the radio](using-x-ctu-to-configure-an-xbee#selectradio).

*TODO*




# Scan wifi channels

On Linux, you can use the command line to check which frequencies are in use by wireless channels. So, with your laptop in the space where you will be performing or setting up your installation perform the command (possibly you need to add `sudo` to the command to perform it as root or administrator):

```
iwlist scan
```

You will see a long list of possible WiFi's; you can filter the information a bit to get the bits that we need:

```
iwlist scan | grep Frequency:
```

You then get a result like this:


    Frequency:2.437 GHz (Channel 6)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.462 GHz (Channel 11)
    Frequency:5.18 GHz (Channel 36)
    Frequency:5.24 GHz (Channel 48)
    Frequency:5.24 GHz (Channel 48)
    Frequency:5.24 GHz (Channel 48)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.462 GHz (Channel 11)
    Frequency:5.24 GHz (Channel 48)
    Frequency:5.2 GHz (Channel 40)
    Frequency:5.24 GHz (Channel 48)
    Frequency:5.5 GHz (Channel 100)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.462 GHz (Channel 11)
    Frequency:5.22 GHz (Channel 44)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.462 GHz (Channel 11)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.412 GHz (Channel 1)
    Frequency:2.437 GHz (Channel 6)
    Frequency:2.437 GHz (Channel 6)
    Frequency:2.437 GHz (Channel 6)
    Frequency:2.437 GHz (Channel 6)
    Frequency:5.18 GHz (Channel 36)
    Frequency:5.22 GHz (Channel 44)


You can save the results to a text file with:

```
iwlist scan | grep Frequency: > wifiscan.txt
```

We are not so interested in the results in the 5 GHz range, so we can ignore. We may also be interested in the signal strength. These are on the line after `Frequency` in the full output, so if we use the command

```
iwlist scan | grep Frequency: -A 1 > wifiscan.txt
```

it will also output the signal strength. We can now reorder the data in the file by channel and throw out the 5 GHz entries.

Then we have an output like:

```
    Frequency:2.412 GHz (Channel 1)
    Quality=34/70  Signal level=-76 dBm  
--
    Frequency:2.412 GHz (Channel 1)
    Quality=32/70  Signal level=-78 dBm  
--
    Frequency:2.412 GHz (Channel 1)
    Quality=36/70  Signal level=-74 dBm  
--

    Frequency:2.437 GHz (Channel 6)
    Quality=64/70  Signal level=-46 dBm  
--
    Frequency:2.437 GHz (Channel 6)
    Quality=61/70  Signal level=-49 dBm  
--
    Frequency:2.437 GHz (Channel 6)
    Quality=60/70  Signal level=-50 dBm  
--
    Frequency:2.437 GHz (Channel 6)
    Quality=58/70  Signal level=-52 dBm  
--

    Frequency:2.462 GHz (Channel 11)
    Quality=31/70  Signal level=-79 dBm  
--
    Frequency:2.462 GHz (Channel 11)
    Quality=36/70  Signal level=-74 dBm  
--
    Frequency:2.462 GHz (Channel 11)
    Quality=35/70  Signal level=-75 dBm  
--
    Frequency:2.462 GHz (Channel 11)
    Quality=36/70  Signal level=-74 dBm  
--
```

Here we see that a lot is happening on channel 6 (strongest signals), and that there are also networks on channel 1 and 11.


# Select XBee channel

The XBee channel is calculated by the formula:

```
2.405 * 1000 + ( (ATCH-11)*5 )
```

The channels that are close to the wifi channels above are: channels 0x10, 0x0B and 0x15. So the best choice of channel is to be away from these channels for example channel `0x0D` (2.415 GHz), `0x13` (2.445 GHz) or `0x19` (2.475 GHz).

You can now configure your XBee with this channel [using X-CTU](using-x-ctu-to-change-settings-of-an-xbee).
