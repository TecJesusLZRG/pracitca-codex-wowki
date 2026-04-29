# Architecture

## Firmware Style
The application is implemented in **Arduino-style C++**, not pure Pico SDK C APIs.
Primary dependencies:
- `Keypad.h` for matrix keypad scanning and debouncing.
- Arduino core GPIO APIs (`pinMode`, `digitalWrite`, `delay`).

## Code Structure (`src/main.cpp`)
- **Pin/Matrix Definitions**
  - `LEDS`, `ROWS`, `COLS`
  - `keys[ROWS][COLS]` keymap
  - `ledPins[]`, `rowPins[]`, `colPins[]`
- **Keypad Object**
  - `Keypad keypad = Keypad(...)`
- **`setup()`**
  - Initializes all LED GPIO pins as outputs and sets LOW.
- **`loop()`**
  - Reads current key via `keypad.getKey()`.
  - Executes `switch` actions to set individual/group LED states.
  - Runs with a `delay(10)` loop period.

## Control Logic Map
- Numeric:
  - `1..8` -> turn ON corresponding blue LED.
  - `9` -> turn ON LEDs 1..8.
  - `0` -> turn OFF LEDs 1..8.
- Alphabetic:
  - `A..D` -> turn ON corresponding red LED.
  - `*` -> turn ON red LEDs A..D.
  - `#` -> turn OFF red LEDs A..D.

## Non-Functional Scope
This repository update focuses on:
- clean folder organization,
- maintainable project documentation,
- preserving existing runtime behavior.

No core logic rewrite or algorithmic change is introduced.
