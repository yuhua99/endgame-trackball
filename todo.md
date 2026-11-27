# TODO

- [x] Encoder height 5.0 → 5.1 mm (TTC 1035111112000): moved the daughter PCB 0.1 mm toward the motherboard (PCB X 33.4–35.0, axis stays at 40.10, H = 5.10). Bottom shell PCB-seat wall face moved 33.5 → 33.4 between the edge-stop ribs (locating pin kept); PCB to motherboard 0.9 mm. In `ttc_encoder_daughter_3d.step` the encoder housing/rotor stay shaft-referenced.
- [x] Rebuild the encoder footprint to the shared TTC/Alps/Kailh pattern (lugs ±4.5, 1.8×2.1, +2.0 from the pin row) and fix the pinout (A −2.5, B 0, C/GND +2.5, lugs toward the FPC).
- [x] Shell fit for the new PCB: the 11.8 mm board's floor-side edge sits at Z 1.3, 0.1 mm into the PCB slot floor (Z 1.4). Lowered both slot floors to Z 1.0 (0.3 mm clearance).
- [x] Encoder body position and lug clearance: the body center sits ~1.0 mm from the pin row toward the lugs, and the lug next to the heat-set insert overlapped the insert. Moved SW1 1.0 mm toward the roller edge (pins PCB y 99 / shell Y 2.6, lugs y 101 / Y 4.6), so the body center stays at Y 3.6 and hex engagement is unchanged; A/B/C labels moved to F.Fab (no room on silk). Bottom shell: old pin pocket filled, new blind pockets 1.0 deep for pins and lugs (pad + 0.3); 0.80 mm wall to the insert hole, 1.45 mm to the locating pin. KiCad 9: DRC 0 / unconnected 0 / parity 0, ERC 1 expected warning.
- [x] Refill the B.Cu GND zone and run KiCad 9 DRC/ERC: DRC 0 / unconnected 0 / parity 0; ERC 1 expected warning (1V8 global label used once).
- [x] J1 pin 1 carries 1V8 like the stock encoder board (unused on this board).
