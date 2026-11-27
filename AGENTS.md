# AGENTS.md

Fork of the efog Endgame trackball: replace the stock encoder with side rollers (one per side wall), driven by a TTC 5.1 mm mouse encoder on a new daughter PCB.

## Layout
- `original/` — stock efog shells (`FDM_shell.step` top, `FDM_bottom.step` bottom). Read-only reference.
- `../endgame-trackball-hardware/` — stock KiCad (separate repo, read-only). Motherboard is rev7 (`trackball.kicad_pcb` in that repo is rev10; outline and encoder FPC are close enough to use as reference); stock encoder board `encoders-upgrade/encoders_upgrade.kicad_pcb` (EC05E encoder + 8P 0.5 mm FPC).
- Repo root — our outputs: `top_side_roller.step`, `bottom_side_roller.step`, `side_roller_d*.step`, `ttc_encoder_daughter.kicad_*`.
- `todo.md` — open work. Read before starting; tick items when done.
- `README.md` — geometry spec, currently stale (e.g. roller X). Measure current values from the STEP files; update README in the same commit as geometry changes.

## Scope
- Change: top/bottom shell, roller, encoder daughter PCB.
- Keep: motherboard, stock floor openings, Z=10.00 mm shell split, everything not touched by the roller.
- One roller + one daughter PCB per side (left and right). Both sides use the same PCB design (no mirrored variant).
- Scroll only; no middle click, so the FPC switch pins stay unused.
- The daughter PCB connects to the motherboard through the stock 8P 0.5 mm FPC and its pinout.

## Manufacturing
- Shells and rollers: JLCPCB MJF nylon (PA12). Size walls, clearances, and press fits for MJF, not FDM.
- Roller is one MJF part (`side_roller_d14.step`): Ø14 grooved drum, Ø4 stub journals at both ends, printed hex shaft into the encoder. Printed hex is intentional: no off-the-shelf metal 1.7 mm hex shaft exists.
- Daughter PCB: JLCPCB, 1.6 mm.
- Hardware (reuse stock parts only): heat-set insert M2×3.5×2.5, M2×4 ISO7380 screw, magnet Ø4×2.

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

## Workflow
- CAD: use the `cad` skill. PCB: use the `pcb` skill.
- KiCad is 9.0 (`CAD_KICAD_CLI=/usr/bin/kicad-cli`) for DRC, ERC, zone refill, and exports. cad's nightly (needed for `kicad_pcb.edit`) does not run here (glibc 2.35 < 2.36), so edit `.kicad_pcb` / `.kicad_sch` as text and keep them in KiCad 9 format.
- Measure fits against `original/` and `endgame_motherboard_3d.step`; report clearances in mm.
- Commit each finished step without asking. Messages use Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`).
