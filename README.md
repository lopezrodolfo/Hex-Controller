# Seven-Segment Hexadecimal Display Controller

This C program controls a hardware multiplexed 7-segment display on a breadboard using a PICOSOC RISC-V processor instantiated on an FPGA.

## Authors

- CEO: Tyson Aramaki
- PM: Frank Veldhuizen
- Dev: Rodolfo Lopez
- Test: Sam Cacino

## Date

11/20/22

## Features

- Displays a 16-bit binary number as 4 hexadecimal digits
- Supports counting up or down based on hardware input
- Handles display updates and timing

## Hardware Interface

The program interfaces with the hardware through GPIO:

- Output: 16-bit value to display (4 hex digits)
- Input:
  - Bit 0: Second toggle signal from display
  - Bit 1: UP/DOWN direction control

## Main Loop

The main loop performs the following actions:

1. Reads the hardware inputs (second toggle and UP/DOWN control)
2. Updates the counter value based on the UP/DOWN input
3. Converts the counter value to minutes and seconds
4. Outputs the time value to the GPIO for display

## Functions

- `convert()`: Alternative function to convert seconds to minutes and seconds without using division or modulo operations

## Notes

- The program is designed for a specific PICOSOC RISC-V implementation
- It assumes a 50 MHz clock for timing calculations
- The display update is triggered by the second toggle signal from the hardware

## Compilation

Compile this program for the target RISC-V architecture. Ensure you have the appropriate toolchain set up for cross-compilation.

## Usage

Load the compiled binary onto the PICOSOC RISC-V processor's memory. The program will start running and controlling the 7-segment display automatically.

## Acknowledgements

The starter code was written by Professor Chuck Pateros. Out team:

- Changed the UP/DOWN signal from pin 23 to pin 25 in `upduino3.pcf`
- Set the colon by instantiating the .XTRA signals in the `display.v`
- Made colon modifications in `top.v`
- Enabled the processor for MULDIV in `Makefile`
- Enabled MULDIV in `top.v`
- Made modifications to use / and % instead of convert() in `firmware.c.`
