---
layout: post
title: "Pressure Scanner Board: Progress II"
author: "Matthew Cox"
categories: journal
tags: [documentation, pressure_scanner]
image: footprintheader.png
---

Today I finished the first draft of the schematic for the MCU dev board. This is officially part of the pressure scanner board project now. Since I am making posts about the progress for this board don't expect to see this over again when I actually get to the pressure scanner. I'm going to just skip right to layout most likely. Here is the pdf of the first draft:

[SAMD21-DevBoard-REV0](/assets/files/SAMD21_DevBoard_REV0.pdf)

I have also completed the BOM and am now finally in the process of assigning and creating footprints for layout. Who would have thought that I would get slowed down by school?

![BOM](/assets/img/devboardbom0.png)

I got pretty lucky and most of the parts I picked either had very standard footprints or I was able to find them online. After quickly verifying all of the ones I found online I checked my BOM and the only parts I have to make footprints for are:

- 32.678 kHz Crystal
- Reset Switch
- USB Micro AB Connector

All of which are relatively easy so I should be doing board layout in no time!

First up: the RTC crystal

![Crystal](/assets/img/crystalpad.png)

Easy, nice warmup. For this one I personally set a custom grid with 1 mm spacing to make things easier.

![crystalfoot](/assets/img/crystalfootprint.png)

Next up: Reset Switch

![Switch](/assets/img/switchpad.png)

Again, relatively easy.

![Switchfoot](/assets/img/switchfootprint.png)

And finally, the USB connector. Then we can get to my favorite part, layout!

This one is going to take me a bit longer than the others haha.

![USBpad](/assets/img/usbpad.png)

After doing it, I can say this is one of the harder footprints I've ever had to do. Knowing 3D modeling definitely came in handy for this one.

![USBfoot](/assets/img/usbfoot.png)

And there you go. All components now have a footprint. Expect another post for layout, that should be a fun one.


