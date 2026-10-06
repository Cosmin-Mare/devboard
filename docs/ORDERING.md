# Ordering from JLCPCB (PCB + assembly)

Files are in `fabrication/jlcpcb/`.

1. Go to <https://jlcpcb.com> → **Order now** → upload `devboard-gerbers.zip`.
2. Board settings that match the design:
   - Layers: **2**, Dimensions: **21.05 × 51.05 mm**
   - Thickness: **1.6 mm**, Surface finish: HASL (lead-free) or ENIG (your choice – the design has no special requirement)
   - Min track/space 0.2 mm, min drill 0.3 mm (standard capability)
3. Enable **PCB Assembly** → **Assemble top side only**. Pick quantity (the saved match was for 5 boards).
4. Upload `bom.csv` and `cpl.csv`. Make sure every row matches the LCSC number in the table below.
5. In the placement preview, check **pin-1 and rotation** of: U1 (RP2040), U2 (MCP1700 SOT-23), U3 (flash), Y1 (crystal), J1 (USB-C), SW1. Fix rotation in the preview if anything looks wrong.
6. J2, J3 (20-pin headers) and J4 (3-pin SWD header) showed **quantity 0** in the saved JLCPCB match – they are through-hole parts you solder yourself (see [ASSEMBLY.md](ASSEMBLY.md)).
7. Review the price and place the order.

## LCSC parts

| Ref | Value | LCSC | Type |
|---|---|---|---|
| C1, C10 | 1 µF 0402 | C52923 | Basic |
| C2–C9, C11, C12, C17 | 100 nF 0402 | C1525 | Basic |
| C13, C14 | 10 µF 0603 | C19702 | Basic |
| C15, C16 | 33 pF 0402 | C1562 | Basic |
| J1 | USB-C (HRO TYPE-C-31-M-12) | C165948 | Extended |
| R1, R2 | 5.1 kΩ 0402 | C25905 | Basic |
| R3, R4 | 27 Ω 0402 | C25100 | Extended |
| R5, R7 | 1 kΩ 0402 | C11702 | Basic |
| R6 | 10 kΩ 0402 | C25744 | Basic |
| SW1 | Tactile 4×3 mm (XUNPU TS-1088-AR02016) | C720477 | Basic |
| U1 | RP2040 | C2040 | Extended |
| U2 | MCP1700T-3302E/TT | C39051 | Extended |
| U3 | W25Q16JVUXIQ | C2843335 | Extended |
| Y1 | 12 MHz 3225 crystal (YXC X322512MSB4SI) | C9002 | Basic |
| J2, J3 *(hand-solder)* | 1×20 pin header 2.54 mm | C50981 | Extended |
| J4 *(hand-solder)* | 1×3 pin header 1.27 mm | C24980 | Extended |

The last saved JLCPCB estimate (2026-10-06, 5 assembled boards) was **~$17.27** for assembly parts; stock and prices change, so re-match before ordering. Extended parts add a per-part loading fee.
