# Wiring and GPIO Mapping

## Components (from `diagram.json`)
- 1x Raspberry Pi Pico / Pico W (`wokwi-pi-pico`)
- 1x 4x4 membrane keypad (`wokwi-membrane-keypad`)
- 12x LEDs (`wokwi-led`)
  - 8x blue (labels 1..8)
  - 4x red (labels A..D)
- 12x LED current-limit resistors, 220 ohm (`r1..r12`)
- 4x keypad pull-up resistors, 1k ohm (`rp1..rp4`)

## Keypad Connections

| Keypad Signal | Pico GPIO |
|---|---|
| C1 | GP19 |
| C2 | GP18 |
| C3 | GP17 |
| C4 | GP16 |
| R1 | GP26 |
| R2 | GP22 |
| R3 | GP21 |
| R4 | GP20 |

Additional wiring in diagram:
- R1..R4 each connected through 1k network (`rp1..rp4`) to **3V3** (pull-ups).

## LED Connections

| Logical LED | Color | Pico GPIO |
|---|---|---|
| LED1 | blue | GP11 |
| LED2 | blue | GP10 |
| LED3 | blue | GP9 |
| LED4 | blue | GP8 |
| LED5 | blue | GP7 |
| LED6 | blue | GP6 |
| LED7 | blue | GP5 |
| LED8 | blue | GP4 |
| LED9 (A) | red | GP3 |
| LED10 (B) | red | GP2 |
| LED11 (C) | red | GP28 |
| LED12 (D) | red | GP27 |

All LED cathodes are tied to **GND**.
Each LED anode is driven through a 220 ohm resistor from its GPIO.

## Notes and Assumptions
- GPIO mapping follows the arrays in `src/main.cpp`; this matches the wiring in the provided Wokwi diagram.
- Diagram part is `wokwi-pi-pico`; logic is valid for Pico W as well (same RP2040 GPIO map).
