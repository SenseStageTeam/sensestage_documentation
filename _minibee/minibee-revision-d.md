---
title: MiniBee Revision D
summary: The MiniBee revision D was the third version of the MiniBee, the production version. It was manufactured and sold between 2011 and 2016.
layout: documentation
type: reference
creation-date: 2017-02-06
category: hardware
subcategory: minibee
related: 
    - Programming firmware with the arduino IDE
    - Prepare the Arduino IDE for use with Sense/Stage
tags:
    - todo
---

![](/img/MiniBee_revD_XBee_header.jpg)


Overview of the board:

* 6 analog inputs: A0, A1, A2, A3, A6, A7
* 8 digital inputs or outputs: D3 and D5 to D11
* PWM (“analog”) output, at pins D3, D5, D6, D9, D10, D11
* I2C communication: SDA (A4), SCL (A5)
* Serial I/O: RX, TX (to XBee)
* Power input (between 3.3V and 5V), through battery connector and coin cell battery
* Regulated power output: 3.3V, GND
* green pcb

# Pins

The pin outs on the header are from left to right:

    GND - RX - D5 - D7 - D9 - D11 - A6 - SDA - A2 - A0
    3v3 - TX - D3 - D6 - D8 - D10 - A7 - SCL - A3 - A1

    
![](/img/minibee_annotated-D-front.jpg)
![](/img/minibee_annotated-D-back.jpg)

# LEDs


# Technical documents

* board layout
* schematic


[Design files for Eagle on github](https://github.com/sensestage/minibee_hardware/tree/master/minibee/revD)

# Changes to previous version

Revision D of the board has a few minor improvements on revision B:

* An additional LED on pin D4 for status indication.
* RX and TX also available on the output pin header.
* All bootloader programming pins broken out in the middle of the board


# Programming firmware and the bootloader

For [programming the firmware](prepare-the-arduino-ide-for-use-with=sense-stage#board), use the board definition: `Sense/Stage MiniBee revB/D/F (3.3V, 12MHz) w/ Atmega328p`


# Subversions {#subversions}

The first manufacturing run has the Atmega328 chip instead of the Atmega328p chip. This is a subtle difference that only affects the board if you want to program the bootloader onto the board, or program firmware without using the bootloader. The boards of this first batch can be recognized by a sticker on the bottom with a serial number, and the desoldered pin holes. In the hardware definitions within the Arduino IDE, this version is called `Sense/Stage MiniBee revD0 (3.3V, 12MHz) w/ Atmega328`. You *only* need this for programming the bootloader or programming the board with the Atmel programmer, not for the regular uploading of firmware.

![](/img/MiniBee_revD0.jpg)

![](/img/MiniBee_revD0_bottom.jpg)


You may also need the section below in the `avrdude.conf` file that is in the `hardware/tools/` folder of your copy of Arduino if you want to program with an AVR programmer onto the chip (e.g. for changing the bootloader, or bypassing it):


```
#------------------------------------------------------------
# ATmega328
#------------------------------------------------------------

part
id = "m328";
desc = "ATMEGA328";
has_debugwire = yes;
flash_instr = 0xB6, 0x01, 0x11;
eeprom_instr = 0xBD, 0xF2, 0xBD, 0xE1, 0xBB, 0xCF, 0xB4, 0x00,
0xBE, 0x01, 0xB6, 0x01, 0xBC, 0x00, 0xBB, 0xBF,
0x99, 0xF9, 0xBB, 0xAF;
stk500_devcode = 0x86;
# avr910_devcode = 0x;
signature = 0x1e 0x95 0x14;
pagel = 0xd7;
bs2 = 0xc2;
chip_erase_delay = 9000;
pgm_enable = "1 0 1 0 1 1 0 0 0 1 0 1 0 0 1 1",
"x x x x x x x x x x x x x x x x";

chip_erase = "1 0 1 0 1 1 0 0 1 0 0 x x x x x",
"x x x x x x x x x x x x x x x x";

timeout = 200;
stabdelay = 100;
cmdexedelay = 25;
synchloops = 32;
bytedelay = 0;
pollindex = 3;
pollvalue = 0x53;
predelay = 1;
postdelay = 1;
pollmethod = 1;

pp_controlstack =
0x0E, 0x1E, 0x0F, 0x1F, 0x2E, 0x3E, 0x2F, 0x3F,
0x4E, 0x5E, 0x4F, 0x5F, 0x6E, 0x7E, 0x6F, 0x7F,
0x66, 0x76, 0x67, 0x77, 0x6A, 0x7A, 0x6B, 0x7B,
0xBE, 0xFD, 0x00, 0x01, 0x00, 0x00, 0x00, 0x00;
hventerstabdelay = 100;
progmodedelay = 0;
latchcycles = 5;
togglevtg = 1;
poweroffdelay = 15;
resetdelayms = 1;
resetdelayus = 0;
hvleavestabdelay = 15;
resetdelay = 15;
chiperasepulsewidth = 0;
chiperasepolltimeout = 10;
programfusepulsewidth = 0;
programfusepolltimeout = 5;
programlockpulsewidth = 0;
programlockpolltimeout = 5;

memory "eeprom"
paged = no;
page_size = 4;
size = 1024;
min_write_delay = 3600;
max_write_delay = 3600;
readback_p1 = 0xff;
readback_p2 = 0xff;
read = " 1 0 1 0 0 0 0 0",
" 0 0 0 x x x a9 a8",
" a7 a6 a5 a4 a3 a2 a1 a0",
" o o o o o o o o";

write = " 1 1 0 0 0 0 0 0",
" 0 0 0 x x x a9 a8",
" a7 a6 a5 a4 a3 a2 a1 a0",
" i i i i i i i i";

loadpage_lo = " 1 1 0 0 0 0 0 1",
" 0 0 0 0 0 0 0 0",
" 0 0 0 0 0 0 a1 a0",
" i i i i i i i i";

writepage = " 1 1 0 0 0 0 1 0",
" 0 0 x x x x a9 a8",
" a7 a6 a5 a4 a3 a2 0 0",
" x x x x x x x x";

mode = 0x41;
delay = 5;
blocksize = 4;
readsize = 256;
;

memory "flash"
paged = yes;
size = 32768;
page_size = 128;
num_pages = 256;
min_write_delay = 4500;
max_write_delay = 4500;
readback_p1 = 0xff;
readback_p2 = 0xff;
read_lo = " 0 0 1 0 0 0 0 0",
" 0 0 a13 a12 a11 a10 a9 a8",
" a7 a6 a5 a4 a3 a2 a1 a0",
" o o o o o o o o";

read_hi = " 0 0 1 0 1 0 0 0",
" 0 0 a13 a12 a11 a10 a9 a8",
" a7 a6 a5 a4 a3 a2 a1 a0",
" o o o o o o o o";

loadpage_lo = " 0 1 0 0 0 0 0 0",
" 0 0 0 x x x x x",
" x x a5 a4 a3 a2 a1 a0",
" i i i i i i i i";

loadpage_hi = " 0 1 0 0 1 0 0 0",
" 0 0 0 x x x x x",
" x x a5 a4 a3 a2 a1 a0",
" i i i i i i i i";

writepage = " 0 1 0 0 1 1 0 0",
" 0 0 a13 a12 a11 a10 a9 a8",
" a7 a6 x x x x x x",
" x x x x x x x x";

mode = 0x41;
delay = 6;
blocksize = 128;
readsize = 256;

;

memory "lfuse"
size = 1;
min_write_delay = 4500;
max_write_delay = 4500;
read = "0 1 0 1 0 0 0 0 0 0 0 0 0 0 0 0",
"x x x x x x x x o o o o o o o o";

write = "1 0 1 0 1 1 0 0 1 0 1 0 0 0 0 0",
"x x x x x x x x i i i i i i i i";
;

memory "hfuse"
size = 1;
min_write_delay = 4500;
max_write_delay = 4500;
read = "0 1 0 1 1 0 0 0 0 0 0 0 1 0 0 0",
"x x x x x x x x o o o o o o o o";

write = "1 0 1 0 1 1 0 0 1 0 1 0 1 0 0 0",
"x x x x x x x x i i i i i i i i";
;

memory "efuse"
size = 1;
min_write_delay = 4500;
max_write_delay = 4500;
read = "0 1 0 1 0 0 0 0 0 0 0 0 1 0 0 0",
"x x x x x x x x x x x x x o o o";

write = "1 0 1 0 1 1 0 0 1 0 1 0 0 1 0 0",
"x x x x x x x x x x x x x i i i";
;

memory "lock"
size = 1;
min_write_delay = 4500;
max_write_delay = 4500;
read = "0 1 0 1 1 0 0 0 0 0 0 0 0 0 0 0",
"x x x x x x x x x x o o o o o o";

write = "1 0 1 0 1 1 0 0 1 1 1 x x x x x",
"x x x x x x x x 1 1 i i i i i i";
;

memory "calibration"
size = 1;
read = "0 0 1 1 1 0 0 0 0 0 0 x x x x x",
"0 0 0 0 0 0 0 0 o o o o o o o o";
;

memory "signature"
size = 3;
read = "0 0 1 1 0 0 0 0 0 0 0 x x x x x",
"x x x x x x a1 a0 o o o o o o o o";
;
;
```