# RP2040 Real-Time Robotics Controller

Lingua Franca firmware labs for the Pololu 3pi+ 2040 robot, developed as part of Arizona State University embedded systems coursework. The repository keeps the original course deliverables, but is organized like a small robotics firmware project: source files, reports, packaged submissions, and working notes are separated by lab.

## Project Scope

This work explores real-time robot control on the Raspberry Pi RP2040 using Lingua Franca reactors and C interop. Across the top-level lab modules, the robot exercises GPIO control, direct peripheral access, sensor polling, interrupt-driven behavior, line sensing, motor control, IMU-based orientation, and autonomous navigation routines.

Key implemented behaviors include:

- LED and serial output exercises for RP2040 toolchain bring-up.
- IMU tilt measurement using accelerometer data and LCD feedback.
- GPIO and memory-mapped I/O examples for low-level peripheral control.
- Interrupt callback, debounce, physical action, and modal behavior examples.
- Line detection and avoidance using the 3pi+ reflectance sensors.
- Hill-climb and track-following controllers using motor, encoder, gyro, and line sensor feedback.

## Hardware And Tooling

- Hardware: Pololu 3pi+ 2040 robot with RP2040 microcontroller.
- Language: Lingua Franca with embedded C reactions.
- Platform target: `rp2040` / `pololu_3pi_2040_robot`.
- Typical tools: Lingua Franca compiler, Pico SDK, CMake, Arm GCC toolchain, and `picotool`.
- Sensors and actuators: LSM6DSO IMU, quadrature encoders, IR line sensors, push buttons, LCD, LEDs, and differential drive motors.

## Repository Layout

```text
.
|-- lab-01-tools/
|   |-- src/
|   |-- report/
|   `-- submission/
|-- lab-02-sensors/
|   |-- src/
|   |-- report/
|   `-- submission/
|-- lab-03-peripherals/
|   |-- src/
|   |-- report/
|   `-- submission/
|-- lab-04-interrupts/
|   |-- src/
|   |-- report/
|   `-- submission/
|-- lab-06-hill-climb/
|   |-- src/
|   |-- report/
|   |-- submission/
|   `-- notes/
|-- lab-07-line-tracking/
|   |-- src/
|   |-- report/
|   `-- submission/
`-- README.md
```

Each top-level lab folder follows the same convention:

- `src/`: Lingua Franca source files for that lab.
- `report/`: submitted report files.
- `submission/`: original packaged course submission archives.
- `notes/`: working notes or experimental code captured during development.

Lab 5 is not present in this repository; the checked-in coursework artifacts jump from Lab 4 to Lab 6.

## Lab Index

| Lab | Focus | Primary source files |
| --- | --- | --- |
| Lab 1 | Toolchain, LEDs, and printf output | `LED.lf`, `ToolsBlinkSolution.lf`, `ToolsLEDSolution.lf`, `ToolsPrintfSolution.lf` |
| Lab 2 | IMU and tilt sensing | `Tilt.lf`, `SensorsTiltSolution.lf` |
| Lab 3 | Peripherals and direct MMIO access | `PeripheralsButtonSolution.lf`, `PeripheralsDirectSolution.lf` |
| Lab 4 | Interrupts, debounce, actions, and modes | `InterruptActionSolution.lf`, `InterruptCallbackSolution.lf`, `InterruptDebouncedSolution.lf`, `InterruptModalSolution.lf` |
| Lab 6 | Hill climbing, line detection, and line avoidance | `HillClimbSolution.lf`, `HillLineDetectSolution.lf`, `HillLineAvoidSolution.lf` |
| Lab 7 | Track following with proportional steering | `TrackFollowSolution.lf` |

## Building And Flashing

The `.lf` files are intended for the Lingua Franca embedded lab environment and depend on the support reactors imported as `lib/*.lf` in that environment. To build one solution, use an LF/Pico workspace where those library imports resolve.

Example workflow after copying a solution into an LF/Pico workspace:

```sh
lfc src/TrackFollowSolution.lf
picotool load -x bin/TrackFollowSolution.elf
```

For example, `lab-07-line-tracking/src/TrackFollowSolution.lf` can be copied into `lf-pico/src/` before running the commands above. Alternatively, adjust the import paths so `lib/Line.lf`, `lib/Motors.lf`, `lib/Display.lf`, `lib/IMU.lf`, and related support reactors are visible.

## References

- [Pololu 3pi+ 2040 User's Guide](https://www.pololu.com/docs/0J86)
- [Pololu 3pi+ 2040 Control Board Schematic](https://www.pololu.com/file/0J1833/3pi-plus-2040-control-board-schematic.pdf)
- [ST LSM6DSO Datasheet](https://www.st.com/resource/en/datasheet/lsm6dso.pdf)
- [Lingua Franca Documentation](https://www.lf-lang.org/)
- [Lingua Franca Embedded Labs](https://www.lf-lang.org/embedded-lab/)

## Coursework Note

This repository began as an ASU lab submission archive. The current layout preserves the submitted artifacts while making the project easier to browse, review, and extend as a robotics firmware portfolio.
