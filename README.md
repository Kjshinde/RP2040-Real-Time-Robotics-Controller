# Autonomous Robot Control System
### Firmware for Pololu 3pi+ 2040 using Lingua Franca

This repository contains the source code for an autonomous mobile robot system developed for the Raspberry Pi RP2040 (ARM Cortex-M0+). The project focuses on high-precision navigation, sensor fusion, and reactive control using the Lingua Franca coordination language.

## 🚀 Key Features
* **Autonomous Hill Climbing:** Uses real-time accelerometer and gyroscope feedback to navigate 15° inclines while maintaining orientation.
* **Precise Navigation:** Implements quadrature encoder-based dead reckoning to execute exact square-path trajectories and 90° turns.
* **Intelligent Obstacle Avoidance:** Multi-modal behavior handling using tactile bump sensors and infrared reflectance sensors.
* **Bare-Metal Performance:** Direct Memory-Mapped I/O (MMIO) register manipulation for low-latency hardware control.
* **Deterministic Execution:** Built on a reactor-based architecture to ensure predictable timing for all control loops.



## 🛠 Tech Stack
* **Language:** C, Lingua Franca (LF)
* **Hardware:** Pololu 3pi+ 2040 (RP2040, Dual-core ARM Cortex-M0+)
* **Sensors:** ST LSM6DSO 6-axis IMU, Quadrature Encoders, IR Line Sensors
* **Toolchain:** CMake, GCC Arm Embedded Toolchain, `picotool`

## 📂 Project Structure
* `/src`: Main application logic for robot missions (Square, Hill Climb, Line Following).
* `/src/lib`: Reusable drivers and reactor components for motors, IMU, and encoders.
* `/bin`: Compiled binary files (UF2/ELF) for flashing to the RP2040.

## ⚙️ Software Architecture
The system is designed using **Modal State Machines**, allowing the robot to switch behaviors dynamically:
1. **DRIVING:** Default state for forward progress using speed control.
2. **AVOIDING:** Triggered by bump sensors; executes a backup and re-orientation sequence.
3. **CALIBRATING:** Initial state for IR sensor normalization.



## 🔗 Hardware Documentation (Pololu 3pi+)
* [Pololu 3pi+ 2040 User's Guide](https://www.pololu.com/docs/0J86) — *Official documentation for robot assembly and pinout.*
* [Control Board Schematic](https://www.pololu.com/file/0J1833/3pi-plus-2040-control-board-schematic.pdf) — *Detailed wiring for GPIO 25 (LED/Button A) and motor drivers.*
* [ST LSM6DSO Datasheet](https://www.st.com/resource/en/datasheet/lsm6dso.pdf) — *Technical specifications for the 6-axis IMU.*

## 🔗 Lab Instructions & LF Resources
* [Lingua Franca (LF) Documentation](https://www.lf-lang.org/)
* [Embedded Lab 04: Interfacing with Sensors](https://www.lf-lang.org/embedded-lab/Sensors.html)
* [Embedded Lab 05: Peripherals & MMIO](https://www.lf-lang.org/embedded-lab/Peripherals.html)
* [Embedded Lab 06: Interrupts & Modal Behavior](https://www.lf-lang.org/embedded-lab/Interrupts.html)
* [Embedded Lab 08: Hill Climb Challenge](https://www.lf-lang.org/embedded-lab/Hill.html)

---
*Developed as part of the Graduate Embedded Systems Curriculum at Arizona State University.*
