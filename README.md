# Klipper TMC2209 Sensorless Homing Issue on Z-Axis

This repository serves as a central point for troubleshooting sensorless homing issues on the Z-axis using **TMC2209 stepper drivers** in a **Klipper firmware** setup. The configuration for the X and Y axes works as expected, but the Z-axis encounters persistent false triggering during the retract phase of homing, despite various tuning efforts.

## Problem Overview

- **Endstop error**: The Z-axis shows "Endstop Z still triggered after retract."
- **TMC2209 `driver_SGTHRS` sensitivity tuning**: Adjusted between 10 to 300 but still encountering issues.
- **Wiring and diag_pin configuration**: Potential issues with `diag_pin` configuration.

## Configuration Summary

### Current Z-axis Configuration:
```ini
[tmc2209 stepper_z]
uart_pin: PC5
run_current: 0.8  # Set down to prevent motor stress (some motors have 0.8A versions)
hold_current: 0.5
interpolate: True
stealthchop_threshold: 1
driver_SGTHRS: 80  # Adjust sensitivity if needed
diag_pin: ^PC3

[tmc2209 stepper_x]
uart_pin: PB9
run_current: 0.9
hold_current: 0.8
interpolate: True
stealthchop_threshold: 1
driver_SGTHRS: 100
diag_pin: ^PC0

[tmc2209 stepper_y]
uart_pin: PD2
run_current: 1.4
hold_current: 0.8
interpolate: True
stealthchop_threshold: 1
driver_SGTHRS: 115
diag_pin: ^PB8

