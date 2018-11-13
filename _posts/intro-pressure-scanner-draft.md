---
layout: post
title: "Pressure Scanner Board: Introduction"
author: "Matthew Cox"
categories: journal
tags: [documentation, independent_study, pressure_scanner]
---

Just wanted to make a quick post introducing the pressure scanner board project I am currently working on before I get too far into the project. 

As mentioned before, this is a project I am taking on for the University of Connecticut Formula SAE team. The main goal of the project is to create a PCB and enclosure to locally test differential pressure at different locations while the car is driving.

The team is developing an aerodynamic package and needs some data to validate their calculations and simulations. Also the judges at the event would rip us apart if we tried to develop an aero package without any testing or data haha.

#### Sensors

The team has already chosen the following sensors:

- 4x DLHR-L10D-E1BD-C-NAV8 Board Mount Pressure Sensors Low Voltage Digital Pressure Sensor, 10 inH2O
- 1x HSCDANN015PA2A5 Board Mount Pressure Sensors DIP,Single Ax Barbed Absolute, 5V

The first sensor was chosen as it is a differential pressure sensor with very high resolution (up to 18 bit) and has a convenient digital interface.

The second sensor was chosen to give a static pressure reading to go along with the differential pressure readgings. It is not very high resolution but provides decent accuracy and also has a digital interface.

Currently we only have purchased 5 sensors but I will be planning on developing the capability for atleast 5 more sensors by adding DIP sockets to the PCB. I am going to assume that the would like to use the same differential pressure sensor but will also include interfaces for other types.

#### MCU

Since these sensors have digital interfaces, some type of microcontroller (MCU) is obviously needed to interface with the sensors. At this point I intend to use the Atmel SAMD21 MCU. This is the same MCU that is found in the Arduino Zero.

By using the same MCU as the Zero, we will be able to load the Arduino bootloader onto the device and use the Arduino IDE for programming. As much as I would like to avoid the Arduino interface, it makes the most sense for this project. This is my last year on the team and I won't be around to debug in the future. If the board has a simple Arduino interface with prewritten libraries and support, the team should be able to debug without me. 

The Arduino IDE is also a lot more forgiving to work with compared to using something like Atmel Studio and the Hardware Abstraction Libraries (HAL) provided there.

The SAMD21 is also decently overpowered for this task which makes it easy for the team to iterate and expand upon my design in the future without worrying about upgrading the MCU.

#### Digital Interfaces

The SAMD21 has 6 SERial COMmunication interfaces (SERCOM) which can be configured as SPI, I2C or UARTs. I plan on using two SPIs and one I2C interface to work with the sensors.

To interface with the CAN Bus network running on our car we will go with the tried and true MCP2551/2515 combo. We are already using this combination on our dashboard with the [Seeed Studio CAN Bus Shield](https://www.seeedstudio.com/CAN-BUS-Shield-V2-p-2921.html) and have had great success with it over the last four years.

The image below is a quick block diagram I came up with for the board:

[PressureScannerBlockDiagram](/assets/img/Proposed_Block_Diagram2.png)

#### Next Steps

In the coming weeks I will be doing the following:

- The board will run off of the unregulated 12V supply that powers the rest of the car so I will need to find parts to provide a 5V and 3.3V regulated supply for the sensors and MCU.
- Determine how frequently each sensor can be read and then determine the ideal speeds for the SPI and I2C clocks. 
- Determine which pins on the SAMD21 can be used as SERCOM modules and begin creating a schematic in KiCAD.
- Start gathering parts on a BOM to track cost.
- Searching or creating footprints for the chosen parts.
- Writing test code using our SAMD21 Dev board once the pressure sensors come in.


Thanks for reading, I look forward to writing more about this project.





