# ECE520-Lab-2
Garrett Ponce

AXI GPIO using Vivado Block Diagrams and Vitis

## Project Abstract

This lab introduced Vitis, and demonstrated how to take block diagrams with GPIO outputs from Vivado, and move them over to Vitis for the firmware to be adjusted. The prelab was a walked through guide that created a baseline for the postlab. The postlab expanded on the prelab by introducing more GPIO outputs, to control 2 outputs and 1 input on the Zybo-20 board. The lab was successful and will be demonstrated on Monday

## Hardware
- Zynq - 7020 Development Board
- 1 USB cable
- Windows 10 Computer with software installed

## Software
- Vivado 2023.2
- Vitis Classis 2023.2

## Prelab Code

### Blinking LED with UART

The prelab code created a guide between Vivado and Vitis, where a block diagram was created on Vivado, and the bitstream hardware was exported to Vitis to manipulate. 

inside Vitis, the "Hello World" code was adjusted to demonstrate an LED switching on and off, and a UART command (seen using the serial terminal) showing when the LED was high and low

Demo will be shown in lab

## Post lab Code

### Vivado Block Diagram
the post lab expands on the prelab by introducing 3 AXI GPIO blocks to the Zynq block. the 3 GPIO blocks had outputs to the following

- GPIO 1 -> LED (outputs)
- GPIO 2 -> RGB (outputs)
- GPIO 3 -> Switches (inputs)

the block diagram is shown below

![Figure 1: Vivado Block Diagram (Post Lab)](https://github.com/gtponce9/ECE520-Lab-2/blob/d97ac195bfb271d766aefb24afc67fc19c21c42d/AXI_GPIO_Instantiation_post_lab.png)

### Vitis Code

Once the Hardware was saved, and Vivado was closed out, I created a new platform and new application for the Vitis code post lab. There are comments describing all the code. Essentially, three different GPIO's instances were made from struct XGpio to call out the three GPIO addresses. Each GPIO was initialized as either inputs or outputs. and lastly a switch statement was made with switches (SW) as the expression to allow each case to be determined off of the switches used. Since a switch statement was used, all scenarios were covered for the switches as shown in the table below.

| Switch                                        | LED Output       | RGB LED            |
|-----------------------------------------------|------------------|--------------------|
| **SW0 = 1**, SW1 = 0, SW2 = 0, SW3 = 0        | LED0 = 1         | Red                |
| SW0 = 0, **SW1 = 1**, SW2 = 0, SW3 = 0        | LED1 = 1         | Green              |
| SW0 = 0, SW1 = 0, **SW2 = 1**, SW3 = 0        | LED2 = 1         | Blue               |
| SW0 = 0, SW1 = 0, SW2 = 0, **SW3 = 1**        | LED3 = 1         | White (R + G + B)  |
| **SW0 = 1**, **SW1 = 1**, SW2 = 0, SW3 = 0    | Binary Counter   | RGB LED OFF        |
| SW0 = 0, SW1 = 0, **SW2 = 1**, **SW3 = 1**    | Ring Counter     | RGB LED OFF        |
| Any other multiple switch combination         | LEDs OFF         | RGB LED OFF        |
| No switches enabled                           | LEDs OFF         | RGB LED OFF        |




## Overview

This lab got me the flu and the hardware issue with the shorting plug not being on the JTAG was very annoying

I remember a 425 lab that was similar to this lab, so it was pretty streamline once I remember it

I had to use chatgpt to remember pointers (still don't make that much sense but I'll ask you to explain it in class)

overall this was very informative and a good introduction to Vitis.

