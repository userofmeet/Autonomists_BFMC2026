🚗 Bosch Future Mobility Challenge — Embedded Platform Setup
📌 Overview

This repository documents my complete setup journey for the Embedded Platform used in the Bosch Future Mobility Challenge (BFMC).

It covers everything needed to bring the microcontroller side of the autonomous vehicle to life:

⚙️ Installing build dependencies

🔧 Configuring toolchains (ARM GCC, CMake, Ninja)

📦 Deploying the correct Mbed OS version

🚗 Preparing the BFMC Embedded Platform

📂 Understanding the project structure

🧪 Compiling and flashing onto NUCLEO-F401RE

This README acts as a future reference for competitors, teammates, and embedded system learners.

🛠 1. Environment Setup
✔️ Install Python (3.6+)
python --version

✔️ Install CMake

Download from official website:

cmake.org/download

✔️ Install Ninja Build System
pip install ninja

✔️ Install Mbed Tools

(Mandatory for building BFMC firmware)

pip install mbed-tools

✔️ Install GNU ARM Toolchain

Required to compile code for the Nucleo-F401RE MCU.

Toolchain recommended by Mbed OS.

📁 2. Clone Embedded Platform Repository
git clone https://github.com/ECC-BFMC/Embedded_Platform.git
cd Embedded_Platform

⚙️ 3. Deploy the Correct Mbed OS Version

This ensures compatibility with the BFMC platform.

mbed-tools deploy


This command automatically downloads:

the exact Mbed OS revision

required libraries

dependency modules

🧪 4. Compile the Firmware
mbed-tools compile -m NUCLEO_F401RE -t GCC_ARM


📌 Output file location:
./BUILD/NUCLEO_F401RE/GCC_ARM/Embedded_Platform.bin

🔌 5. Flash the Microcontroller
Option 1: Auto-flash during build
mbed-tools compile --flash

Option 2: Manual flashing

Drag-and-drop the .bin onto the Nucleo USB drive.

🗂 Project Structure
📁 Embedded_Platform
 ┣ 📁 mbed-os/                # Auto-downloaded Mbed OS core
 ┣ 📁 src/                    # Source code (sensors, actuators, logic)
 ┣ 📁 configs/                # Project + Mbed configuration files
 ┣ 📄 CMakeLists.txt          # Build definitions
 ┗ 📄 README.md               # (This file)

🧱 Architecture Diagram
    ┌──────────────────────────────┐
    │      NUCLEO-F401RE Board     │
    └─────────────┬────────────────┘
                  │
        ┌─────────▼─────────┐
        │     Mbed OS       │
        └─────────┬─────────┘
                  │
 ┌────────────────▼────────────────┐
 │  Sensors → Motor Control → CAN  │
 └────────────────┬────────────────┘
                  │
          Autonomous Vehicle

🚗 Why This Matters

The embedded platform serves as the brainstem of the BFMC autonomous vehicle.

It controls:

steering

acceleration

braking

lane following

sensor interpretation

emergency logic

Without this firmware, the car cannot perform any navigation tasks.

🧑‍💻 Developed By

Harshid Bhupendra Rawal
Department of Electronics & Communication
Dharmsinh Desai University, Nadiad

Domains:
Robotics • Embedded Systems • Computer Vision • Autonomous Navigation
