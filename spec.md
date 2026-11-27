# Part specs

Dimensions of the parts we buy or reuse, with sources. Model geometry (positions, clearances) lives in the STEP and KiCad files, not here.

## Encoder: TTC 1035111112000
TTC (Huizhou Trantek) 103 series conventional encoder, through shaft (直通轴). Sold as "TTC 藍芯 5mm"; official installation height is 5.1 mm (TTC has no 5.0 mm part).
- 24 detents / 12 pulses, A/B two-phase, hex bore 1.74±0.02 mm, torque 14–26 gf·cm.
- Outline: `ref/ttc_103_drawing.png` (TTC, from https://www.ttc9.com/productdetails/34.html). "安装脚距 11.60" is the splayed lug-tip width, not the PCB hole spacing. Installation height = PCB surface to shaft center.
- TTC publishes no PCB layout. TTC 103 / E203, Alps EC10E and Kailh mouse encoders share one mounting pattern (drop-in interchangeable); use it:

```
signal pins  3 × Ø1.0 hole, pitch 2.5 (A, B, C)
lug holes    2 × 1.8 (X) × 2.1 (Y), centers at X = ±4.5
             lug row offset 2.0 from the signal pin row (toward the body)
```
  Sources: `ref/alps_ec10e_mounting_holes.png`, `ref/alps_ec10e_dimensions.png` (Alps EC10E catalog), `ref/kailh_cen975512r13_pcb_layout.png` (Kailh 5.5 mm spec, same numbers).
- Pinout: common C is an end pin, not the middle. Alps front view reads A B C. Working reference footprint (github.com/christrotter/mouse-encoder-pcb, tested with Alps/TTC/Kailh), top view: lugs at Y=+1, pins at Y=−1, A at X=−2.5, B at 0, C (GND) at X=+2.5. Swapping A/B only reverses scroll direction.

## Fasteners and magnets
Stock efog hardware, reused.
- Heat-set insert M2×3.5×2.5: OD 3.5, length 2.5.
- Magnet Ø4×2.

## M2 self-tap hole
Trilobe hole for an M2 screw tapping directly into MJF PA12, copied from the BTU-base screw holes in `bottom_side_roller.step` (e.g. at X −23.7, Y 16.0): inscribed Ø1.4, outer Ø2.2. Reuse this profile wherever a screw taps into the shell.

## Daughter PCB
- FR-4, 1.6 mm, JLCPCB.
- FPC connector: JS AFH34-S08FIA-1H, 8P 0.5 mm pitch (stock pinout).
