---
layout: post
title: "Lessons Learned: Ego is the Enemy"
author: "Matthew Cox"
categories: journal
tags: [documentation, VHDL]
image: fp_bd.png
---

Sometimes you get to a point where your ego is too big and it needs to be kicked down a notch, or like 10... 

This is a story of how I got super full of myself and almost absolutely failed my final project for the Digital Systems Design using FPGAs class I took this semester.

First, a little background. I am taking this class where we are utilizing a FPGA training board (Nexys 4 DDR) to complete a bunch of basic labs to learn about VHDL and exercise design skills.

I have really been enjoying this class this semester, except for the fact that it takes up so much of my time. Every week I was spending upwards of 6-8 hours working on these labs. 

I was doing pretty well throughout the semester and generally getting things done pretty quickly. I enjoy this stuff and even though it takes forever and the tools are terrible, its pretty fun. 

We covered topics such as: 7 segment displays, Finite State Machines (FSM), VGA, PS/2, PWM, AXI Bus, Embedded MCUs and Block RAM. For the final project we were supposed to pick something that incorporated these topics. One kid did a maze, another did a basic piano and someone else did a basic excel sheet. Lots of cool projects.

When it came to picking the project I had absolutely no idea what I was going to do. I knew there was an accelerometer on the board and I thought: "Oh I can just use this and visualize the motion on the VGA display". The professor mentioned it might be hard but I was so full of myself that I told him I would figure it out. 

I regret this so much now.

#### Error 1: Picking something that we didn't even cover in a lab during the semester. 

However, it got so much worse from there. 

I had originally assumed the accelerometer was a simple sensor which would feed into one of the analog inputs on the board. I knew there was a built in Analog to Digital converter and knew some Vivado IP already existed for this.

I looked up the accelerometer data sheet and this is when I realized I was screwed. It turns out the sensor interfaces through Serial Peripheral Interface (SPI) and was pretty complex. It required the user to write commands to an internal register in order to retrieve the data at certain intervals.

At this point I SHOULD have gone to the professor and tried to figure out another project, but no. I instead found a SPI module written by the board manufacturer and told myself I could make it work.

#### Error 2: Moving forward with complex HDL that I didn't write with such a short time frame.

At this point it would be super cool to say that I got everything to work and everything ended up all peachy but this is not what happened.

To further mess myself up, I put the project on the back burner while I finished the rest of my work load for the semester. 

This was actually kind of worth it though, I did end up getting A's in every class but this one.

#### Error 3: Leaving the project until 3 days before it was due.

I spent those three days doing absolutely nothing but this project and made little to no progress. The code I found for the SPI module was way too complex and when I tried to make a test bench for it, it didn't really work that well.

So on demo day I went to the professor and told him I totally messed up. Luckily not many people had finished the project at this point and he extended the deadline from Friday to Sunday. With one catch: You lost 10% each day...

At this point I was so in the gutter but he told me a could print a box on the screen and move it with the keyboard instead of the accelerometer. Thank God, I should have done something like this from the start.

I spent the next 24 hours doing nothing but this project and submitted it late Saturday night. It was the furthest thing from my best work and I am really not proud of the final product. Its kind of embarassing but I got what I deserved.

I ended up with a 72/100 on the project and still managed to pull an A- in the class but suffered all of finals week.

#### Lesson Learned: Stop trying to show off for school projects

Playing with the accelerometer is something I should have done in my free time and maybe I'll revisit it during winter break or next semester.

#### Lesson Learned: Don't use other people's code without spending time understanding it first

This was just silly. I shouldn't have used it at all since I couldn't even write a testbench for it...

#### Lesson Learned: Start earlier

I shouldn't even have to write this, I know this all too well.


This definitely kicked my ego down which is what I needed. Lesson definitely learned on this one.
