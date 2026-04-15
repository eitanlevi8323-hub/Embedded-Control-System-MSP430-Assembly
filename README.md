# MSP430 Assembly Embedded Project (Lab 5)

This repository contains an embedded software project written in Assembly for the TI MSP430 microcontroller. The project implements a multi-state embedded application using timers, interrupts, and an LCD interface.

## Architecture
The code is structured into four distinct layers (modules) to ensure modularity and clean separation of concerns:

1. **MAIN (`main_lab5.s43`)**: Contains the primary Finite State Machine (FSM) that dictates the program flow based on user inputs.
2. **API (`api_lab5.s43`)**: Provides high-level logical functions, such as 16-bit multiplication/division routines, UI logic for the LCD timer, and frequency formatting.
3. **HAL (`hal_lab5.s43`)**: The Hardware Abstraction Layer. Implements reusable functions for interfacing with hardware peripherals like sending commands/strings to the LCD and debouncing push buttons.
4. **BSP (`bsp_lab5.s43`)**: The Board Support Package. Handles low-level microcontroller initialization, GPIO setup, clock/timer configurations, and Interrupt Service Routines (ISRs).

## Key Features

The system operates in a low-power mode (LPM0) by default and wakes up upon button presses to execute one of the following features:

- **1-Minute Countdown Timer (State 1)**: Triggered by PB0. A timer counts down from 01:00 to 00:00 and updates the LCD in real-time.
- **Frequency Measurement (State 2)**: Triggered by PB1. Utilizes Timer Capture Module to measure an external incoming digital signal's frequency and displays the result on the LCD (in Hz).
- **Variable PWM Generator (State 3)**: Triggered by PB2. Generates a Pulse Width Modulation (PWM) signal on Port 2.3, dynamically adjusting its frequency.

## Tools
- Assembly Language `.s43` (Ti MSP430 Architecture)
- Developed for IAR Embedded Workbench / TI Code Composer Studio.
