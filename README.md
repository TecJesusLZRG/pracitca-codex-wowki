# Raspberry Pi Pico W 4x4 Keypad + 12 LED Controller

## Overview
This project targets the **Raspberry Pi Pico W (RP2040)** and implements keypad-driven LED control logic.
A **4x4 membrane keypad** is read and mapped to **12 discrete LEDs**.

The firmware source provided is **Arduino-style C++** (uses `Keypad.h`, `pinMode`, `digitalWrite`, `delay`).
Core logic has been preserved and moved into `src/main.cpp` without behavior changes.

## Repository Structure

- `src/main.cpp` - original application logic (preserved).
- `src/CMakeLists.txt` - source-level CMake placeholder.
- `include/` - reserved for headers if project grows.
- `docs/wiring.md` - wiring, components, GPIO mapping.
- `docs/architecture.md` - architecture and module explanation.
- `CMakeLists.txt` - top-level project metadata.

## Features
- Reads keypresses from a 4x4 matrix keypad.
- Controls 8 blue LEDs (numeric group) and 4 red LEDs (alpha group).
- Supports grouped LED actions:
  - `9`: turn ON LEDs 1-8
  - `0`: turn OFF LEDs 1-8
  - `*`: turn ON LEDs A-D
  - `#`: turn OFF LEDs A-D

## Build/Flash Options

## Option A: Wokwi Simulation (recommended for this exact source)
1. Create a new **Raspberry Pi Pico** project in Wokwi.
2. Use the provided `diagram.json` wiring.
3. Use the Arduino sketch equivalent of `src/main.cpp`.
4. Ensure `Keypad` library is available in Wokwi libraries.
5. Run simulation.

## Option B: Real Hardware with Arduino IDE / PlatformIO
1. Install **Arduino-Pico** core for RP2040 boards.
2. Select board: **Raspberry Pi Pico W**.
3. Install library: **Keypad** by Mark Stanley / Alexander Brevig.
4. Copy `src/main.cpp` logic into an Arduino sketch (`.ino`) or configure PlatformIO.
5. Put Pico W into BOOTSEL mode and flash.

## Option C: Pico SDK (pure C/C++)
The current source is not Pico SDK-native. To use pure Pico SDK, APIs must be ported (outside this documentation-only scope).

## Flashing Pico W (UF2 workflow)
1. Hold **BOOTSEL** while connecting Pico W via USB.
2. Device mounts as `RPI-RP2`.
3. Copy generated `.uf2` from Arduino/PlatformIO build output.
4. Board reboots and runs firmware.

## Wi-Fi Note
This project does **not** use Wi-Fi features. No credentials are required.
If Wi-Fi is added later, store credentials in an ignored config file (for example `secrets.h`) and never commit secrets.

## Behavior Preservation
No functional changes were made to key handling or LED state logic.
Only repository layout and documentation were added.
