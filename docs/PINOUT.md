# Pinout

Two 20-pin 2.54 mm headers, 17.78 mm apart (same as a Raspberry Pi Pico). **Pin 1 is the end nearest the USB-C connector.** This is *not* the Pico pin order – pins are in the order below.

| Pin | J2 (left) | J3 (right) |
|---:|---|---|
| 1 | GPIO0 | VBUS (5 V from USB) |
| 2 | GPIO1 | GPIO29 / ADC3 |
| 3 | GND | GND |
| 4 | GPIO2 | GPIO28 / ADC2 |
| 5 | GPIO3 | +3V3 (regulator output) |
| 6 | GPIO4 | GPIO27 / ADC1 |
| 7 | GPIO5 | GPIO26 / ADC0 |
| 8 | GND | GND |
| 9 | GPIO6 | GPIO24 |
| 10 | GPIO7 | GPIO23 |
| 11 | GPIO8 | RUN (pull low to reset) |
| 12 | GPIO9 | GPIO22 |
| 13 | GND | GND |
| 14 | GPIO10 | GPIO21 |
| 15 | GPIO11 | GPIO20 |
| 16 | GPIO12 | GPIO19 |
| 17 | GPIO13 | GPIO18 |
| 18 | GND | GND |
| 19 | GPIO14 | GPIO17 |
| 20 | GPIO15 | GPIO16 |

**J4 – SWD (1.27 mm, 3-pin):** 1 = SWCLK, 2 = GND, 3 = SWDIO.

Notes
- GPIO29/ADC3 also senses VSYS on a Pico; here it is a free pin.
- GPIO24 and GPIO23 are exposed; GPIO25 (Pico's LED) is not.
- The 3V3 rail is from a 250 mA LDO shared with the RP2040 – budget accordingly.
