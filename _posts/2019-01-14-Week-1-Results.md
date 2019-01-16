---
layout: post
title: "Independent Study: Week 1"
author: "Matthew Cox"
categories: journal
tags: [documentation,independent_study]
image: waveform.png
---

Week 1 of my documented independent study has officially died down and didn't quite go as expected. While I did get a lot of work done, most of it was not for the independent study. 

I spent a lot of time picking up the slack for my Senior Design project. While I still don't want to reveal too much about this project, I found myself working on a variety of analog design topics this week.

I spent a good amount of time learning about switching power supplies, specifically buck converters. The board we are designing has a high input voltage (16V - 32V range) and requires a buck supply to give usable power rails for the MCU and other circuits on the board.

I also found myself researching a bunch of information about how to design reliable current sources. Our board needs one of these as well and I have not had the pleasure of designing one of these before.

Finally, I came up with a cool power shutdown circuit which involved some low side current sensing. Would love to show it here but I can't. :(

So I did end up doing work for the independent study but it went a bit differently than I expected. The first thing I tried to do was complete the readings that I had assigned to myself. 

This didn't go so well. 

These readings were interesting but not the kind of stuff I need to know to work on microcontrollers. Most it was a bunch of stuffy computer architecture theory. I may forgo reading from this book altogether throughout the rest of the semester but we will see about that.

The thing I spent the most time on this week was FPGA stuff. I ended up writing the beginnings of a SPI module in VHDL. The goal here is to eventually interface with the accelerometer on board the FPGA dev board and get some readings from there. 

[SPI Module](https://github.com/mcox53/Independent-Study-Spring19/tree/master/VHDL/SPI)

I have a busy week ahead, including an interview, so I may not get much further. I have already written a basic test bench and am currently debugging the state machine. 

This week I will probably do a bit of assembly and look for more interesting reading. At some point I may compile a list of all the web resources I used when working on these projects. I'm talking like raw google searches and stack overflow links. That is all part of the learning process.

While it wasn't what I planned I think we are off to a decent start here. Cheers to the next week!