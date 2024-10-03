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
run_current: 0.8 # I've set this down not to abuse the motor, there are 0.8a version on some of these machines.
hold_current: 0.5
interpolate: True
stealthchop_threshold: 1
driver_SGTHRS: 80  # Adjust sensitivity if needed
diag_pin: ^PC3
