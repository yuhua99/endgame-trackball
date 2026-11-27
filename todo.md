# TODO

- [x] Encoder height 5.0 → 5.1 mm (TTC 1035111112000): moved the daughter PCB 0.1 mm toward the motherboard (PCB X 33.4–35.0, axis stays at 40.10, H = 5.10). Bottom shell PCB-seat wall face moved 33.5 → 33.4 between the edge-stop ribs (locating pin kept); PCB to motherboard 0.9 mm. In `ttc_encoder_daughter_3d.step` only the PCB, FPC connector and passive moved; the encoder housing/rotor stay shaft-referenced until the body-position item rebuilds them.
- [x] Rebuild the encoder footprint to the shared TTC/Alps/Kailh pattern (lugs ±4.5, 1.8×2.1, +2.0 from the pin row) and fix the pinout (A −2.5, B 0, C/GND +2.5, lugs toward the FPC).
- [x] Shell fit for the new PCB: the 11.8 mm board's floor-side edge sits at Z 1.3, 0.1 mm into the PCB slot floor (Z 1.4). Lowered both slot floors to Z 1.0 (0.3 mm clearance).
- [ ] Encoder body position: with the real footprint (Alps geometry), the body center sits ~0.9 mm from the pin row toward the FPC (shell +Y), not on the pin row as `ttc_encoder_daughter_3d.step` models it. Re-check roller hex engagement and the body-to-roller gap, and update the 3D STEP. The wall pocket behind the PCB (Y 2.8–4.4, Z 1.8–11.4) only clears the signal pins; the real lugs sit at Y ≈ 5.6, Z 2.7 / 11.7 and need their own relief (the current lug model already overlaps the pocket sides by 0.1 mm).
- [x] Refill the B.Cu GND zone and run KiCad 9 DRC/ERC: DRC 0 / unconnected 0 / parity 0; ERC 1 expected warning (1V8 global label used once).
- [x] J1 pin 1 carries 1V8 like the stock encoder board (unused on this board).
