cmake_minimum_required(VERSION 3.13)
project(pico_w_keypad_led C CXX)

# NOTE:
# The provided source uses Arduino APIs (pinMode, digitalWrite, delay, Keypad.h).
# Build this project with an Arduino-compatible RP2040 core (e.g., Arduino-Pico),
# or adapt to Pico SDK APIs if a pure Pico SDK build is required.

add_subdirectory(src)
