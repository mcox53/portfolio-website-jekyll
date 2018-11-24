---
layout: post
title: "Pressure Scanner Board: Progress I"
author: "Matthew Cox"
categories: journal
tags: [documentation, independent_study, pressure_scanner]
image: mcu_kicad.png
---

Since the last time I posted about the board a good amount of stuff has happened. My teammate and I have shifted our focus to working on the layout and setup of the MCU. This is a critical step because we will buying an SAMD21 off the shelf and then loading the arduino bootloader onto it ourselves. The following considerations come into play:

- What is the minimum amount of discrete components needed to run the MCU? (XTAL, caps, resistors, fuses, etc..)
- How do we program the MCU if the USB interface and bootloader is not setup?
	- What do we use to program the board?
	- Do we need to buy an external programmer?
- What type of power supply is required?

Since we are so unsure about all of this, I volunteered to design our own SAMD21 dev board. The whole point of doing this is so that we can prove the process of designing and setting up an MCU from off the shelf. We will hopefully be desigining more custom PCBs with the SAMD21 in the future so proving our process is important to us. 

Once we solidify this, the MCU of any future project should be an afterthought.

Why?

We can just grab and copy all of the IP from this project (code, schematic, footprint, parts list, etc) and drag it into the new project. This will let us focus on the important parts of the project and not worry about setup.

So I guess the pressure scanner board is technically on the back burner for now but like I said this is relevant to all projects, current and future, so it still relates.

Now to answer the questions and show what we have so far:

#### Question: Minimum amount of components to run the MCU?

This one was honestly pretty easy. For this we just referred to the datasheet as well as existing, open source boards that use a SAMD21. This includes the official dev board from Atmel, the Arduino Zero board, and two Arduino SAMD21 boards from Sparkfun.

The following pictures are from the SAMD Datasheet and some values have been chosen based on the other boards as mentioned:

![SAMD21_Layout](/assets/img/mcu_kicad.png)

This is all pretty routine stuff and all of this is reflected in the datasheet:

![Decoupling](/assets/img/samd21ps.png)
![Oscillator Layout](/assets/img/samd21crystal.png)

The only thing that is missing is to chose the exact parts to use for the board. For this, theres no point trying to reinvent the wheel so we will just grab the same parts from the other boards.

#### Question: Programming a bare chip?

So I think I have this figured out but I'm not entirely sure. This seems like the best way to do it when there is no Embedded Debugger chip (EDBG) on board like the genuine Arduino's have.

1. Download the Arduino SAMD21 .hex bootloader file from [Github](https://github.com/arduino/ArduinoCore-samd)
2. Buy a Segger J-Link Debugger or equivalent (Atmel ICE). Or [perform surgery on an Arduino Zero](https://www.avdweb.nl/arduino/samd21/samd21-programmer)
3. Connect the J-Link to the SWD Port on the target board
4. Create a new project in Atmel Studio
5. Use the Device Programming menu to verify the correct fuse settings
6. Load the .hex file into the flash memory.
7. Done?

#### Question: Power Supply?

For the pressure scanner board I have gone ahead and assumed that an 800mA supply will be sufficient for the entire board. After all, there is nothing that requires significant power on the board. If anything 800mA is overkill.

This comes in the form of the following:
- [LM1117 800mA Low Dropout Linear Regulator](http://www.ti.com/lit/ds/symlink/lm1117.pdf)

Nothing much to say here. It fits the bill for the unregulated 12V battery input (more like 13.5V usually).

- [AP2112 600mA LDO Regulator](https://www.diodes.com/assets/Datasheets/AP2112.pdf)

This may get bumped down based on some further analysis of sensor loads. Here is what I have so far:

![Power Supply](/assets/img/ps_kicad.png)

#### Other

Pressure sensors have come in! If I have some free time I might slap these on a breadboard and try to read some data and then prototype a library. 

I have been told these sensors are touchy and if you send the wrong command you corrupt the sensor. I will make sure to whip out our trusty Saleae Logic 8 to check the packet data before connecting the sensors.

#### What's Next?

- Finish MCU breakout board
	- Complete schematic
	- Complete BOM
	- Find or make footprints for parts on BOM
	- Board Layout
	- Design Review
	- Purchase board, stencil and parts
- Pressure Scanner
	- Finally get to making a table for SERCOM pins

That's all for today. Happy Thanksgiving!
	





