---
layout: post
title: "Lessons Learned: Clocks n' Stuff"
author: "Matthew Cox"
categories: journal
tags: [documentation, lessons_learned, arm]
image: clock_sync.png
---

Do you ever struggle with a problem and then when you figure out the solution it just hits you in the face like:

![duh](/assets/img/duh.jpg)

Yeah well I swear this happens to me all the time when working on these side projects.

So thats what these posts are going to be about. Obvious mistakes or things I forgot to do. Fun right?

So today's event happened while I was trying to run some demo code on a new dev board. the dev board is an Atmel ARM Cortex M0+ and this is the first time I have had the pleasure of using an ARM core. It is also the first time I have used the Atmel Advanced Software Framework for anything other than blinking LEDs on a board.

For this trial I decided to take some demo code and modify it in order to get acquainted with the setup and operation of the peripheral in question. Now the demo code was available from the Atmel ASF documentation site so I just simply copied this into my main.c file. 

Where I went wrong are the configuration files. within the ASF, there are modules you import that act as drivers for different peripherals or operation of the MCU. You import the modules you need for the project. If a module requires configuration it will drop a xxx_conf.h file into the src/config folder in your project.

![config_files](/assets/img/config_files.png)

First mistake: Apparently you have to configure these yourself. 

Me over an hour ago thought: "Oh it'll just have the necessary configuration settings to start the peripheral and then I can modify the instance struct later" 

No. Not even close. 

With ARM and ASF (mostly ASF) there are a million settings and configuration files just to get the board up and running. Coming from programming an atmega328p on the regular, this seems wild to me but I guess its necessary given the jump to a 32-bit architecture.

So I spent the first 30 minutes trying to figure out why my UART was not displaying anything even though I had configure it according to the documentation. While doing so I tried out the Serial Wire Debug interface and I am in love. I wish setting up Debug Wire on the 328p was as easy as using the SWD interface.

This is where I got wind that it wasn't getting past the setup stage. I then read more of the ASF documentation and realized that I needed to configure the clock. :/

I finally found some clock settings for the peripheral demo I was using and recompiled. For some reason it still wasn't getting past setup and synchronizing with the PLL.

![clock_sync](/assets/img/clock_sync.png)

I probably spent another 30-45min debugging before I FINALLY figured out the error.

So the conf_clocks.h exposes 9 general clock generators (GLCK) to use for the main system or with peripherals. The settings I found on the internet had settings to setup the 48MHz system clock using the Digital Phase Locked Loop (DPLL) and to provide a reference using the external 32kHz crystal.

None of the other GCLK generators were used. Or so I thought...

After comapring every single line of every relevant include file. I finally scrolled down in conf_clocks.h and noticed that the setup code had the 8th GLCK generator turned on...

I changed the flag to turn it on and recompiled all while swearing about the things I would do if this was what fixed my problem.

And what do you know, it fixed it...

![missing_clock](/assets/img/missingclock.png)

#### Lesson Learned: Never skip over parts of your config files.

Just because they dont use the other 6 GCLK generators before it doesnt mean they won't use the last one.

I am still not sure what this last general clock is being used for. I dug through the config files for the peripherals I am using and they all seem to be using GLCK0. Even UART which wasn't printing to the terminal when this was broken.

![usart_config](/assets/img/usart_config_defaults.png)

I have a lot of learning to do...

