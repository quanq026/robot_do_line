# ESP32 Line Follower Robot

This repository contains the Arduino code and documentation for an ESP32-based line follower robot. The robot uses five digital IR sensors to detect a black line on a white surface and controls two DC motors via PWM signals.

## Table of Contents

* [Features](#features)
* [Hardware Requirements](#hardware-requirements)
* [Pin Configuration](#pin-configuration)
* [Circuit Diagram](#circuit-diagram)
* [Installation](#installation)
* [Usage](#usage)
* [Code Overview](#code-overview)
* [License](#license)

## Features

* 5 IR sensors for line detection
* PWM speed control for precise motor control
* Automatic turning and adjusting based on sensor input

## Hardware Requirements

* ESP32 development board
* 2 × DC motors with driver (e.g., L298N, L9110, or similar)
* 5 × IR line tracking sensors
* Jumper wires
* Power supply (battery pack or USB)

## Pin Configuration

| Name             | ESP32 Pin | Description                        |
| ---------------- | --------- | ---------------------------------- |
| S1               | 4         | Leftmost IR sensor (digital input) |
| S2               | 16        | Second sensor                      |
| S3               | 17        | Center sensor                      |
| S4               | 5         | Fourth sensor                      |
| S5               | 18        | Rightmost sensor                   |
| IN1/IN2          | 14, 12    | Direction control for left motor   |
| ENA (PWM\_LEFT)  | 25        | PWM speed control for left motor   |
| IN3/IN4          | 27, 26    | Direction control for right motor  |
| ENB (PWM\_RIGHT) | 33        | PWM speed control for right motor  |

## Circuit Diagram

1. Connect each IR sensor output to the corresponding ESP32 digital pin (4, 16, 17, 5, 18).
2. Connect motor driver inputs IN1, IN2 to ESP32 pins 14, 12.
3. Connect motor driver inputs IN3, IN4 to ESP32 pins 27, 26.
4. Connect ENA to pin 25 and ENB to pin 33 for PWM control.
5. Power the motors and ESP32 according to their voltage requirements.

## Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/<your-username>/esp32-line-follower.git
   cd esp32-line-follower
   ```

2. Open `line_follower.ino` in the Arduino IDE or VS Code with PlatformIO.

3. Select the correct ESP32 board and port.

4. Upload the code to your ESP32.

## Usage

1. Place the robot on a track with a clear black line on a white background.
2. Power on the ESP32 and motors.
3. The robot will automatically read sensor values and follow the line.
4. Use serial monitor (baud rate 115200) to view sensor locations and debug information.

## Code Overview

* **`read_sensor()`**: Reads the five digital sensors and determines the line position. Calls appropriate turn or forward functions.
* **Turning functions (`retrai1`, `retrai2`, `rephai1`, `rephai2`)**: Adjust motor speeds for left or right turns.
* **`dithang()`**: Moves forward at set speed.
* **`dunglai()`**: Stops the robot.
* **`control()`**: Applies PWM values and direction to motors, constrains speeds.
* **`loop()`**: Main loop calling sensor reading and motor control every 10 ms.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
