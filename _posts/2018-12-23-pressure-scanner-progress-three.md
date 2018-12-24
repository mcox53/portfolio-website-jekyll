---
layout: post
title: "Pressure Scanner Board: Progress: III"
author: "Matthew Cox"
categories: journal
tags: [documentation, pressure_scanner]
image: routev2.png
---

After much delay, I present to you the second version of the routing for the MCU dev board. I skipped over version one because I actually forgot to take a screenshot of it before I redid it. 

If you've been living under a rock or just haven't read my website (I'm assuming the later here) this board is a test of our team's ability to develop our own designs using the SAMD21. Basically, its just an experiment in board design and layout so we don't mess up important stuff.

The dimensions of this board are: 44 mm x 60 mm. This was done in order to accomodate a standard breadboard 2.54mm spacing. The header pin connectors that flank the board are set at a width of exactly 40.64 mm apart. This is designed to fit perfectly in our standard double wide breadboard where the board itself will sit over the power and ground rails that run in the middle where the two breadboards meet.

The previous design was 20.32 mm wide. I followed the dimensions of an ESP32 module that I had lying around as it seemed like a good form factor for a dev board. However, after spending some time routing, it was clear that it was going to be impossible to finish. 

Unlike these other smaller dev boards, I tried to utilize parts with footprints as large as possible. For example, when another dev board would opt for an 0806 or an 0604 size capacitor, I always went with the 1210 if possible. 

Even with these choices there is still going to be some issues when it comes time for us to solder everything but it should be a bit more manageable. The sacrifice of going to larger sizes meant that the dimensions of the board had to be expanded. 

Once expanded, the complexity of routing went down significantly.

The board was designed with two flood planes: one for 3.3V and one for GND. Much of the routing was done on the top of the board in order to reduce the complexity.

I attempted to perform the layout and routing in stages (obviously). The USB connector is placed at the top. From here in the top left, is the board power supply. The USB VBUS signal or the VIN signal will travel to the voltage regulator, go through decoupling capacitors and then supply to the 3.3V plane or travel to the MCU. 

Hopefully separating the analog electronics and the digital stuff will reduce noise but since this is a two layer board I am not expecting perfection here.

Some other design choices in this board:
* TX, RX and PWR LEDS at bottom of the board
* Cortex debug connector at bottom of the board
* Reset switch in the top right of the board

[Github Board Repository](https://github.com/mcox53/SAMD21-Dev-Board)

Before I send this board out to be produced, I will have it checked over by my teammates and maybe even reroute some traces. It seems like I have a good amount of space left in some parts and other parts tend to be super crowded.

This is my first PCB of this complexity and I'm sure there is something I did poorly or wrong here. All the more reason to check it over thoroughly.

With the completion of this, I will be moving on to the pressure scanner board and eventually testing of this board. My independent study starts soon and that should bring some fun times and posts! So until then Happy Holiday's from no ones favorite workaholic :)