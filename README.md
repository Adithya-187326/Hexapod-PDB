# Overview
This shield was designed as part of a hexapod robot to be a central controller board that operates on high currents to control 18 servos around an Arduino MEGA microcontroller development board. The working sections of the printed circuit board are broken down into the following areas:
- Power Distribution
- Arduino MEGA Development Breakout Section
- NRF24L01 Connect Provision


# Power Distribution
There are 18 servos used in the bot, with each leg having three servos. Each leg has three different joints: Coaxial, Femur, and Tibia. Of the three, the Femur joint servo motor draws the most current because it outputs the highest torque. Thus, the 6 Femur joints are powered from one power source, and the other 12 joints altogether are powered by another source (both of which are commonly grounded).
During the operation of the bot, the following observations were made using a clamp meter:
- The peak continuous current drawn from the source when one of the Femur motors was operating was around 4A, with a maximum overshoot of 6A for approximately 100 milliseconds.
- The peak continuous current draw from the source, when one of the Coaxial and Tibia motors was operated, was around 4A, with a maximum overshoot of 5A for around 200 milliseconds.

With this being the observation, the board was designed to operate and be able to handle 5A continuous currents with a temperature rise of around 36&deg;C through the power lines. The trace width of the power lines and the voltage drop across the lines were calculated based on formulae published in IPC-2221 [parameters assigned are well within the formulae's range of use], are 50 mils and around 0.3V. Almost all the workable surface is part of the ground plane for better thermal dissipation. The inputs are drawn from buck converters whose outputs are adjusted to 7.4V.

10$`\mu`$F capacitors are placed across the power pins of the servos for decoupling and filtering noise in the supply voltage.

The Arduino MEGA draws power from one of the XT-60 connectors on board. Thus, the **absolute maximum voltage input to the PCB is 12V for the safe operation** of the microcontroller board and peripherals.


# Arduino MEGA Development Breakout Section
The spacing for header pin rows was made based on the design of the Arduino MEGA board. Accessible and well-labeled output points of all pins (not in use) were given for other uses, being faithful to the original design of the microcontroller board, making the PCB a development shield.
All 15 PWM capable pins have their accessible outlet at headers, which connect to the servo motors, along with three other digital pins that would emulate PWM signals using a library. Some pins like AREF, IOREF, 5V, GND, RX0, and TX0 do not have accessible outlets.


# NRF24L01 Connect Provision
The bot can navigate distances and unknown terrains, communicating to a command unit using an NRF24L01 module. A few of the pins that are used for SPI communication have been given outlets in a specific 2x4 grid based on the pinout of the module used, allowing an NRF24L01 module to be plugged into the 2x4 female header grid and deployed for use on board.

# Links and Files
This repository has the images of the topside and bottomside of the board. The link to the OSHW Lab Project is attached below:

Link: https://oshwlab.com/adithyavnarayanan/hexapod

