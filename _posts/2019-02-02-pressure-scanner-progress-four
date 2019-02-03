---
layout: post
title: "Pressure Scanner Board: Progress IV"
author: "Matthew Cox"
categories: journal
tags: [documentation, pressure_scanner]
image: samd21rev0.jpg
---

After quite the long wait, the board was finally sent out a few weeks ago and all of the parts arrived last Thursday. The minimum order quantity for the boards was 5 but I only bought enough parts for two boards just in case something major had to be revised. 

Gary and I spent a good amount of time soldering all of the components on the board as this was the first time I had ever done hot air soldering. Thankfully, I didn't mess things up too badly. There were no lost of ruined components.

I royally messed up the MCU IC twice and after sucking up all the excess solder paste and redoing it, I finally got a nice fit.

Beyond that, there were a few other errors to fix with my solder job and the board was finally assembled! It isn't very pretty, but its a big milestone for me and also the team in general.

The next day I spent a good few hours probing the board to make sure there were no shorts and that everything was connected properly. After a pretty thorough check I plugged it in and nothing blew up!

I was also quite relieved to see that the board was recognized by Atmel Studio and our Segger J-Link debugger when I connected it to the SWD pins.

From there I tracked down the quickest bootloader I could find and rushed to flash it. This proved to take longer than I expected as it turned out the micro USB cable I had lying around was a power only cable.

So after a few hours of trying to debug pins and recompile the bootloader, the board finally showed up on my computer when I borrowed someones phone charger. From there I was able to flash a simple blinking LED sketch using the SparkFun board files. For now we just have to compare pin numbers until we make our own board support package and get it setup.

But it works! The picture at the top of the post is the board running the Arduino equivalent of "Hello, World!"

This opens up UConn Formula SAE to a wide variety of custom designed electronics!

Some quick notes about the board:

- I must have forgot to update the reset switch footprint when I picked out a new switch because it was way too big. The switch I bought fits, with an excess of solder paste applied...
- Same thing with the crystal footprint. The crystal barely fits and I trimmed down the leads significantly.
- You really only need the tiniest bit of solder paste to get the MCU right. Next time I'll just tin the pads and call it a day.
- The silkscreen on the back of the board got cut off slightly due the drilled holes for the pin headers
- I should have come up with a better labeling system for the pins besides just stating the pin number. I might customize the board files in Arduino to try to make it easier for others to understand which pins I am talking about.
- The Micro USB connector chosen is very tiny and tough to solder correctly. I have seen better connectors on other dev boards that have the USB pins sticking out further from the package. I would swap this in a future revision.

To-Do List:

- Compile the UF2 bootloader for the SAMD21 and get rid of the outdated SAM-BA bootloader currently running.
- Create a board support package for the Arduino IDE that contains pin mapping and naming.
- Solder and assemble another board using the remaining set of components.
- Use the two boards to prototype upcoming projects, namely the pressue scanner and dasboard.

I apologize for the gap in posts, I will post an update about the independent study soon.

