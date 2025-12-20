# 🛠️ BFMC: Embedded Platform Setup Guide
[![Platform: Mbed OS](https://img.shields.io/badge/Platform-Mbed--OS-blue.svg)](https://os.mbed.com/)
[![Board: Nucleo-F401RE](https://img.shields.io/badge/Board-Nucleo--F401RE-red.svg)](https://www.st.com/en/evaluation-tools/nucleo-f401re.html)

This document provides a step-by-step guide to configuring your environment for the **Bosch Future Mobility Challenge** embedded platform.

---

## 📋 1. Preliminary Setup
Before you initiate the building process, ensure your environment is correctly configured. 

> [!IMPORTANT]
> All installations should use **Python 3.6+**. 
> Administrative privileges may be required for some steps.

### 🔧 Required Tools

| Tool | Purpose | Link |
| :--- | :--- | :--- |
| **Python 3.6+** | Scripting & Package Management | [Download](https://www.python.org/downloads/) |
| **CMake** | Build Process Management | [Download](https://cmake.org/download/) |
| **GNU Arm Toolchain** | Cross-compiler for Nucleo-F401RE | [Download](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads) |

---

## 💻 2. Installation Steps

### 🔹 Ninja & Mbed-tools
Ninja focuses on build speed, while `mbed-tools` is essential for managing the project structure. Run the following in your terminal:

```bash
# Install Ninja build system
pip install ninja

# Install Mbed-tools
pip install mbed-tools

# Install formatting tools for build output
pip install prettytable intelhex
