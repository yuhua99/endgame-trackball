# endgame-trackball
Side scroll wheel redesign for the Endgame trackball: top/bottom shells, Ø14×20 mm side rollers, and vertical-wall encoder daughter PCBs.

## Current Hardware & Geometry Spec
- **Encoder**: **TTC Blue core, 5.0 mm height** (`H = 5.0 mm`, vertical DIP, 1.74 mm hex bore, 24 detents / 12 pulses, 2.5 mm signal pin pitch, ±5.0 mm mounting lugs — drop-in EC10E footprint on `ttc_encoder_daughter.kicad_pcb`).
- **Side rollers**: Ø14.0 × 20 mm grooved printed rollers (`side_roller_d14.step`) at `X = ±40.60 mm`, `Z = 7.20 mm`, `Y_drum = [-20.90, -0.90]` (+2.45 mm proud of the flat `X = ±45.15 mm` outer wall, untouched 2.20 mm stock bottom floor, 0.75 mm below the top shell's lower outer-button flexure hinge).
- **Daughter PCB retention**: Inner vertical wall mount (`|X| = 34.00..35.60 mm`, 1.50 mm clear of motherboard), 1× M2×4 screw into M2×3.5×2.5 heat-set insert + molded Ø2.0 locating pin + edge-stop ribs.
- **Shells**: Z = 10.00 mm split, 0.8 mm alignment lip, C0.6 seam chamfer, 14.4 mm inverted-U USB-C arch, reset pinhole, old lower-corner encoder openings closed flush, and exact stock bottom floor openings preserved.
