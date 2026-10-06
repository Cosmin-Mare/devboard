# Assembly

## What JLCPCB places (top side)
All SMD parts: U1 RP2040, U2 LDO, U3 flash, Y1 crystal, J1 USB-C, SW1 BOOTSEL button, and all resistors/capacitors (R1–R7, C1–C17).

## What you solder
| Part | Notes |
|---|---|
| J2, J3 – 1×20 header, 2.54 mm | Solder from the **bottom** if you want pins down (breadboard use) or top for pins up. Use a breadboard or a second header to hold them straight and parallel; the rows are 17.78 mm apart. |
| J4 – 1×3 header, 1.27 mm | Optional. Only needed for SWD debugging. |

Tools: soldering iron (~330 °C), leaded or lead-free solder, flux, a breadboard to align headers.

### Steps
1. Inspect the board under magnification: USB-C shell pins, RP2040 QFN pins (no bridges), flash chip.
2. Press the 20-pin headers into a breadboard (long pins down), place the PCB on top, solder one pin per header, check they're square, then solder the rest.
3. Optionally solder J4.
4. Clean flux (isopropyl alcohol + brush).
5. Continue with [BRINGUP.md](BRINGUP.md).

## Circuit summary (for debugging)
- **USB:** J1 D+/D− → 27 Ω series resistors (R4/R3) → RP2040 USB pins. CC1/CC2 each pulled to GND with 5.1 kΩ (R1/R2) so a USB-C host supplies 5 V.
- **Power:** VBUS → C13 10 µF → MCP1700-3.3 (U2) → +3V3 with C14 10 µF. 11 × 100 nF + 2 × 1 µF decoupling around U1.
- **Clock:** 12 MHz crystal Y1 with 33 pF load caps (C15, C16); R5 1 kΩ in series on XOUT.
- **Flash:** U3 on QSPI (SS, SCLK, SD0–SD3).
- **BOOTSEL:** SW1 pulls QSPI_SS to GND through R7 (1 kΩ); R6 10 kΩ pulls QSPI_SS to 3V3.
- **RUN:** brought out on J3 pin 11, no reset button.
