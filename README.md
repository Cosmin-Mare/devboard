# RP2040 Dev Board

A small, Pico-style development board built around the **RP2040**, designed in **KiCad 10**. USB-C, 3.3 V LDO, 2 MB QSPI flash, a BOOTSEL button, SWD header, and every GPIO broken out to two 20-pin 2.54 mm headers. Made to be ordered fully assembled from JLCPCB.

<img width="430" height="693" alt="Screenshot 2026-10-06 at 7 39 09 PM" src="https://github.com/user-attachments/assets/d1d044a3-cbfd-4cc0-aff4-fda08f90d25e" />
<img width="1166" height="798" alt="Screenshot 2026-10-06 at 7 42 24 PM" src="https://github.com/user-attachments/assets/10e541af-9b77-4718-94fd-038abe339ec0" />

| | |
|---|---|
| MCU | Raspberry Pi RP2040 (QFN-56), 12 MHz crystal |
| Flash | Winbond W25Q16JV, 16 Mbit (2 MB) QSPI |
| Power | USB-C (5 V) → MCP1700-3.3 LDO (250 mA) |
| I/O | 26 GPIO (incl. 4 ADC), RUN, VBUS, 3V3, GND on headers; 3-pin SWD (1.27 mm) |
| Controls | BOOTSEL button (no reset button – RUN is on a header pin) |
| Board | 21 × 51 mm, 2-layer, 1.6 mm, headers 17.78 mm (700 mil) apart |
| Assembly | All SMD on the top side (JLCPCB), pin headers hand-soldered |

## Repository layout

```
hardware/kicad/        KiCad 10 project (schematic + PCB) – the source of truth
fabrication/gerbers/   Gerbers, drill files, .gbrjob exported from KiCad
fabrication/jlcpcb/    Ready-to-upload files: gerbers zip, bom.csv, cpl.csv
fabrication/extras/    IPC-D-356 netlist, ODB++, IPC-2581 XML, KiCad board report (.rpt)
bom/bom.csv            Full BOM with MPN + LCSC numbers
bom/BOM.md             Readable BOM
bom/jlcpcb-bom-match-*.xlsx   JLCPCB's BOM-tool match result (stock/prices at the time)
docs/ORDERING.md       Step-by-step JLCPCB order
docs/ASSEMBLY.md       What JLCPCB places vs. what you solder, plus hand-assembly notes
docs/BRINGUP.md       First power-up, flashing, and test checklist
docs/PINOUT.md         Header pinout
```

## Quick start

1. **Order** – follow [docs/ORDERING.md](docs/ORDERING.md). Upload `fabrication/jlcpcb/devboard-gerbers.zip`, then `bom.csv` and `cpl.csv`.
2. **Solder** the two 20-pin headers (and optionally the SWD header) – see [docs/ASSEMBLY.md](docs/ASSEMBLY.md).
3. **Bring up** – hold BOOTSEL, plug in USB-C, copy a `.uf2` onto the `RPI-RP2` drive. See [docs/BRINGUP.md](docs/BRINGUP.md).

## Editing the design

Open `hardware/kicad/devboard.kicad_pro` in KiCad 10. After changes, re-export Gerbers/drill (`File → Fabrication Outputs`), and the position file (`Fabrication Outputs → Component Placement`, CSV, SMD only, millimetres), then refresh `fabrication/` and `bom/`.

## Known notes / things to check before a re-order

- The schematic value for U3 reads `W25Q16JVZPIQ TR`, but JLCPCB matched `W25Q16JVUXIQ` (LCSC C2843335), which is the USON-8 3×2 mm variant matching the footprint. Consider correcting the schematic value so the BOM and part agree.
- JLCPCB's BOM tool flagged several passives as "comment does not match" (value text differs from the part description). The matches are the intended values; review once in the order preview.
- Always check part rotations in JLCPCB's 3D/placement preview (USB-C, RP2040 pin-1, regulator, crystal) before paying – CPL rotation conventions differ between KiCad and JLCPCB.
- No power LED, user LED or reset button are fitted.

## License

MIT for documentation and files in this repo unless you decide otherwise – see [LICENSE](LICENSE). (Open-hardware licences such as CERN-OHL-P-2.0 are a common alternative for hardware; swap it in if you prefer.)

Author: Cosmin Tudor Mare
