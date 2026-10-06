# Bring-up checklist

Before first power-up (no USB):
- [ ] Multimeter continuity: **+3V3 ↔ GND** and **VBUS ↔ GND** are *not* shorted (expect high resistance / charging cap).
- [ ] Visual check of RP2040 and USB-C solder joints.

First power-up:
- [ ] Plug USB-C into a PC. VBUS (J3 pin 1) ≈ 5 V; +3V3 (J3 pin 5) ≈ 3.3 V.
- [ ] If the 3V3 rail is wrong or the regulator is hot, unplug and re-inspect U2 orientation, C13/C14 and U1 power pins.

Flash firmware:
- [ ] Hold **BOOTSEL (SW1)**, plug in USB-C, release. A drive named **RPI-RP2** should appear.
- [ ] Drag a `.uf2` onto it (e.g. MicroPython or Pico SDK `blink`). Note: there is **no onboard LED**; blink a GPIO with an external LED + resistor (e.g. GPIO15 on J2 pin 20).
- [ ] If no drive appears: check the 12 MHz crystal, the flash (U3) solder joints, USB D+/D− (27 Ω resistors) and CC resistors.

Optional SWD:
- [ ] J4 pins: SWCLK, GND, SWDIO. Use a Raspberry Pi Debug Probe or picoprobe.
