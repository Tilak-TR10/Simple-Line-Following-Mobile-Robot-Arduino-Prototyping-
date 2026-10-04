# Simple Line Following Mobile Robot (Arduino Prototyping)

[![Platform](https://img.shields.io/badge/Platform-Arduino%20Uno-blue.svg)](https://www.arduino.cc/)
[![Language](https://img.shields.io/badge/Language-Embedded%20C%2B%2B-brightgreen.svg)](https://en.wikipedia.org/wiki/C%2B%2B)
[![Timeline](https://img.shields.io/badge/Timeline-2015--2018-orange.svg)](https://github.com/)
[![Video Demo](https://img.shields.io/badge/YouTube-Video%20Demo-red.svg)](https://youtu.be/9YvKuH4kBAc)

An autonomous differential-drive mobile robot engineered to track high-contrast tracks using a multi-channel infrared (IR) reflectance sensor bar, dual H-bridge motor actuation, and deterministic Arduino microcontroller logic. This project represents the foundation of my engineering journey in embedded systems, power management, and autonomous robotics prototyping.

---

## 📽️ Video Demonstration

[![Smart Line Following Robot Using Arduino](https://img.youtube.com/vi/9YvKuH4kBAc/0.jpg)](https://youtu.be/9YvKuH4kBAc)

> **Direct YouTube Link:** [Smart Line Following Robot Using Arduino](https://youtu.be/9YvKuH4kBAc)  
> *Click the image above or link to watch the mobile robot navigate high-curvature bends, tight loops, and 90-degree turns autonomously.*

---

## 🌟 Key Highlights

* **Multi-Channel Optical Sensing:** Integrated a front-mounted multi-channel IR sensor bar (with active indicator LEDs) to sample lateral track deviations with high spatial resolution compared to basic 2-sensor setups.
* **Deterministic Course Correction:** Programmed state-based embedded C/C++ control logic that dynamically maps active sensor indices to proportional differential wheel velocities, maintaining centerline alignment.
* **Differential Drive Steering:** Utilized dual geared DC motors paired with an L298N dual H-bridge driver to execute smooth gradual curves, pivot spins, and sharp $90^\circ$ turn recoveries.
* **Power Rail Decoupling:** Implemented separate power supplies for the high-draw motor driver rail and sensitive Arduino logic to prevent inductive kickback resets during rapid motor reversals.
* **Rapid Hardware Prototyping:** Assembled on a rigid dual-deck chassis with a low-friction front support, ensuring stability across floor surface irregularities.

---

## 📐 System Architecture
       +-----------------------------+
       |  High-Contrast Track (Tape) |
       +-----------------------------+
                      │
                      ▼ (Reflected IR)
       +-----------------------------+
       | Multi-Channel IR Sensor Bar |
       +-----------------------------+
                      │
                      ▼ (Digital States)
       +-----------------------------+
       |      Arduino Uno (MCU)      |
       |  Tracking & Steering Logic  |
       +-----------------------------+
                      │
                      ▼ (PWM & Direction)
       +-----------------------------+
       |   L298N Dual Motor Driver   |
       +-----------------------------+
                      │
                      ▼ (High-Current Drive)
       +-----------------------------+
       |    Left & Right DC Motors   |
       +-----------------------------+

---

## 🛠️️ Hardware Bill of Materials (BOM)

| Component | Description | Function |
| :--- | :--- | :--- |
| **Arduino Uno** | ATmega328P 8-bit Microcontroller | Main compute and control logic |
| **IR Sensor Bar** | 4/5-Channel TCRT5000 IR Sensor Module | Surface line detection and boundary sensing |
| **L298N Module** | Dual H-Bridge Motor Driver | Direction and speed control of drive motors |
| **Geared DC Motors** | 3V–6V BO Motors (x2) | Left and right differential drive wheels |
| **Robot Chassis** | Dual-wheel mobile chassis + omnidirectional glide | Physical structure and payload support |
| **Battery Power** | Independent battery pack (9V logic + multi-cell motor pack) | System power supply |

---

## 🔌 Pinout Mapping

| Arduino Uno Pin | Peripheral Connection | Signal Description |
| :--- | :--- | :--- |
| `D2` – `D6` | IR Sensor Channel Outputs | Multi-channel digital sensor inputs |
| `D7`, `D8` | L298N `IN1`, `IN2` | Left motor direction |
| `D9` | L298N `ENA` | Left motor PWM speed |
| `D10` | L298N `ENB` | Right motor PWM speed |
| `D11`, `D12` | L298N `IN3`, `IN4` | Right motor direction |
| `5V` & `GND` | Sensor Rail & Common Ground | Shared reference ground and logic power |
